> 阅读资料
>
> - https://www.baeldung.com/jackson-advanced-annotations
>
> - spring boot jackson case insensitive

:::tip

为什么？可能需要看源码深究

:::

在 **`Controller`** 层使用 **`@RequestBody`** 来得到 `Json` 对象时，如果业务需要 `Json` 的属性**大写**，不能遵守小驼峰命名规范的话，需要特殊处理，例

```json
{
	"Status": "example"
}
```

```java
@Data
@Builder
@NoArgsConstructor
@AllArgsConstructor
public class ExampleDTO {
    // 如果没有JsonProperty显式声明的话，直接将对象的属性名大写，则会直接得到Null值
    @JsonProperty("Status")
    String status;
}
```

```java
@PostMapping(value = "/upload/complete")
public void example(@RequestBody ExampleDTO exampleDto) {

}
```

