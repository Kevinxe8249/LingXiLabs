# 使用 Amazon Corretto 8 作为基础镜像
FROM amazoncorretto:8

# 添加标签
LABEL maintainer="凌曦安全"
LABEL description="CC6 反序列化靶场"
LABEL version="1.0.0"

# 创建应用目录
WORKDIR /app

# 复制已编译好的 jar 包
COPY target/cc6-range-1.0.0.jar app.jar

# 安装 curl 用于健康检查
RUN yum install -y curl && yum clean all

# 暴露端口
EXPOSE 8080

# 健康检查
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
  CMD curl -f http://localhost:8080/ || exit 1

# 启动应用
ENTRYPOINT ["java", "-jar", "app.jar"]
