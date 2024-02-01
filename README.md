# SCOW For AI 适配器配置文件
当前版本中，我们提供了调度器适配器的试用版本的二进制文件[scow-ai-adapter-amd64](https://mirrors.pku.edu.cn/scow/releases/)，欢迎下载进行试用。

在**K8S调度器适配器**所在目录中配置以下信息。其中提交作业的模版文件，创建service的模板文件的示例请参考本项目中的配置文件

```yaml title="config/config.yaml"

dbconfig:
  host: 127.0.0.1              # Mysql数据库服务器地址
  port: 3306                   # 数据库端口
  dbname: ai_db                # 数据库库名
  username: root               # 连接数据库用户
  password: 81SLURM@@rabGTjN7  # 数据库密码

ldapconfig:
  ldapurl: "ldap://localhost:389"          # ldap服务端地址
  bindmanagerdn: "cn=Manager,ou=hpc,o=organizationName" # 管理员dn
  bindmanagerpasswd: "admin"               # 管理员密码
  binduserdn: "ou=People,ou=hpc,o=organizationName"     # 用户dn

adapterport: 8972     # 自定义适配器端口
clusterName: dev-k8s  # 集群名字 需与集群配置中名称一致

jobssourcefilepath: /root/xxxx/job-example.yaml        # 提交作业的模版文件的绝对路径
gpujobssourcefilepath: /root/xxxx/job-example-gpu.yaml # 提交作业的模版文件的绝对路径
jobdestdirectory: /tmp                                 # 存放提交yaml文件的目录
jobsvctemplatefilepath: /root/xxxx/job-service.yaml    # 创建service的模版文件的绝对路径

```

启动适配器及运维适配器与`slurm`适配器相同。请注意适配器所在路径及二进制文件名称变更，命令参考[启动管理slurm适配器](scow-slurm-adapter/docs/deploy.md at master · PKUHPC/scow-slurm-adapter)。
