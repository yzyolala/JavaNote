在开发业务之前需要将用到的类和接口创建好

1.实体类Dish.java

2.Mapper接口DishMapper

```java
@Mapper
public interface DishMapper extends BaseMapper<Dish> {
}
```

3.业务层接口DishService

```java
public interface DishService extends IService<Dish> {
}
```

4.业务层接口实现类DishServiceImpl

```java
@Service
@Slf4j
public class DishServiceImpl extends ServiceImpl<DishMapper, Dish> implements DishService{
}
```

5.控制成DishController

```java
@RestController
@RequestMapping("/category")
@Slf4j
public class CategoryController {
    @Autowired
    private CategoryService categoryService;

    //新增分类
    @PostMapping
    public R<String> save(@RequestBody Category category){
        log.info("Add new category {}",category);
        categoryService.save(category);
        return R.success("Adding new category successfully");
    }

    //分页查询
    @GetMapping("/page")
    public R<Page> page(int page,int pageSize){
        //分页构造器
        Page<Category> pageInfo=new Page<>(page,pageSize);
        //条件构造器
        LambdaQueryWrapper<Category> queryWrapper= new LambdaQueryWrapper<>();
        //添加排序条件，根据sort进行排序
        queryWrapper.orderByAsc(Category::getSort);
        //进行分页查询
        categoryService.page(pageInfo,queryWrapper);
        return R.success(pageInfo);
    }

    //根据id删除分类
    @DeleteMapping
    public R<String> delete(Long ids){
        log.info("Delete category,the id is {}",ids);

//      categoryService.removeById(ids);//removeId方法是mybatis plus中的IService提供的
        categoryService.remove(ids);
        return R.success("Delete the category successfully");
    }
    //根据id修改分类信息
    @PutMapping
    public R<String> update(@RequestBody Category category){
        log.info("Edit the category information:{}",category);
        categoryService.updateById(category);
        return R.success("Edit the information of category successfully.");
    }
}
```
