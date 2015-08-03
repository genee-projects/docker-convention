# docker image 版本规范

> 为解决线上 `docker image` 版本错误发布问题, 故规范 `docker image` 版本

## 规范列表

1. 所有线上发布的版本不可发布 latest 版本, 应为具体的版本号. 例如: `genee/redis:latest` 为错误版本号

2. 所偶 docker 容器版本与代码版本一直。代码版本遵循如下规则:

	* 代码版本使用 [语义化版本](http://semver.org) 进行管理
	* docker 容器版本需要在代码版本后增加 -d、构建时间、当日构建次数, 例如: v2.1.2-d2015080301

3. 针对非自行开发的 docker 镜像版本, 使用安装的 docker 内的服务的版本来标志。例如 `genee/sphinsearch` 版本使用的是 **2.2.9** 版本的 sphinxsearch 服务. 故镜像版本为 `genee/sphinxsearch:v2.2.9-d2015080301`

4. 所有 nodejs 服务都基于 `node:0.12` 进行构建

5. 所有基础服务 (例如 redis, beanstalkd 等), 都基于 `debian 8` 进行构建

6. docker image 进行 volume 挂载时, 应考虑默认挂载目录为 `/home/genee/` 目录对应服务的目录. 

	例如: `genee/redis` 挂载的 volume 为 `/home/genee/redis/` 下的目录
	
7. Lims2-autodeploy 中也应该标注依赖的 docker 服务版本, 针对未标注版本的站点, **不予** 升级/部署!
