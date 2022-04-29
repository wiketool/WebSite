```sql
select user.u_id       userid,
       user.u_username username
from fotilo_star star
         left join fotilo_user user on star.s_star_user_id = user.u_id 										and user.u_is_deleted = 0
where star.s_from_user_id = 37
  and star.s_status = 1
  and star.s_delete = 0
  
```

观察上面的SQL乍一看好像没有问题，实则暗藏玄机，当所关注的用户在数据库中被逻辑删除时，由于Left Join保留左表全部内容，会将右边置空NULL，所以返回的数值也自然是NULL

下面是当前的解决方案

```sql
select user.u_id       userid,
       user.u_username username
from fotilo_star star
         left join fotilo_user user on star.s_star_user_id = user.u_id
where star.s_from_user_id = 37
  and star.s_status = 1
  and star.s_delete = 0
  and user.u_is_deleted = 0
```
