##### reference
<https://docs.microsoft.com/zh-cn/ef/ef6/modeling/code-first/workflows/existing-database>

##### Code First 到现有数据库
* 项目-> "添加新项 ..."
* 从左侧菜单中选择 "数据"，然后ADO.NET 实体数据模型
* 输入 "bloggingcontext" 作为名称，然后单击 "确定"
* 这将启动实体数据模型向导
* 选择 "从数据库 Code First "，然后单击 "下一步"

##### main
```
class Program
{
    static void Main(string[] args)
    {
        using (var db = new BloggingContext())
        {
            // Create and save a new Blog
            Console.Write("Enter a name for a new Blog: ");
            var name = Console.ReadLine();

            var blog = new Blog { Name = name };
            db.Blogs.Add(blog);
            db.SaveChanges();

            // Display all Blogs from the database
            var query = from b in db.Blogs
                        orderby b.Name
                        select b;

            Console.WriteLine("All blogs in the database:");
            foreach (var item in query)
            {
                Console.WriteLine(item.Name);
            }

            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```
