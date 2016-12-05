# KingLion.WebUtils.Jobs

Asp .Net Core��Ŀ�У��ǳ��������첽�������ģ�顣
> ��Ҫ֧�ֽ��ȹ���ʧ�����ԡ�������еȸ߼����ܣ��Ƽ�ʹ��[Hangfire](http://hangfire.io/)

### ��װ

NuGet: 
```
Install-Package KingLion.WebUtils.Jobs
```

### �÷�

1. ����Job Manager
    
    * Startup-> ConfigureServices��
    ```C#
    services.AddJobManager();
   ```
    * Startup-> Configure����������־ģ�����ӣ�
    ```C#
    app.UseJobManager(5000);
    ```
2. �����ҵ
    * ע��IJobManager��
    * �����ҵ��
    ```C#
    _jobManager.Add(() =>
    {
        Thread.Sleep(5000);
        return new JobResult();
    }, (id,result) =>
    {
        _logger.LogInformation($"task{id} completed");
    });
    ```
### ����
* "Microsoft.AspNetCore.Http.Abstractions": "1.1.0",
* "Microsoft.Extensions.DependencyInjection.Abstractions": "1.1.0",
* "Microsoft.Extensions.Logging.Abstractions": "1.1.0",
* "NETStandard.Library": "1.6.1",
* "System.Threading.Thread": "4.3.0"
