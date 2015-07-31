# docker image 版本规范

> 为解决线上 `docker image` 版本错误发布问题, 故规范 `docker image` 版本

## 规范列表

1. 线上 docker image 版本使用 [语义化版本](http://semver.org) 进行管理

2. 所有线上发布的版本不可发布 latest 版本, 应为具体的版本号. 例如: `genee/redis:latest` 为错误版本号, 正确版本应为 `genee/redis:1.0`

3. 所有 docker 容器版本均应与代码版本一致。不允许出现 `genee/epc-server:3.2` 版本而实际代码版本为 **1.2** 版本.

4. 针对非自行开发的 docker 镜像版本, 使用安装的 docker 内的服务的版本来标志。例如 `genee/sphinsearch` 版本使用的是 **2.2.9** 版本的 sphinxsearch 服务. 故镜像版本为 `genee/sphinxsearch:2.2.9`

5. 所有 nodejs 服务都基于 `node:0.12` 进行构建

6. 所有基础服务 (例如 redis, beanstalkd 等), 都基于 `debian 8` 进行构建

7. docker image 进行 volume 挂载时, 应考虑默认挂载目录为 `/home/genee/` 目录对应服务的目录. 

	例如: `genee/redis` 挂载的 volume 为 `/home/genee/redis/` 下的目录
	
8. Lims2-autodeploy 中也应该标注依赖的 docker 服务版本, 针对未标注版本的站点, **不予** 升级/部署!
