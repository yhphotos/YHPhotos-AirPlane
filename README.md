# YHPhotos - 新一代航空资源网站

YHPhotos 是一个专业的航空摄影分享平台，支持真实飞行照片和模拟飞行截图的上传、审核、分享和管理。

## 功能特点

### 核心功能
- **用户系统**：注册、登录、邮箱验证
- **照片上传**：支持详细的飞机信息标注
- **自动水印**：上传时自动添加版权水印
- **审核系统**：管理员审核机制
- **分类管理**：多种航空分类和图片类型
- **搜索功能**：按标题、注册号、机型等搜索
- **用户主页**：个人照片展示页面
- **统计功能**：浏览、点赞、下载统计

### 模拟飞行专区
- 独立的模拟飞行图片上传和展示区域
- 支持多种飞行模拟器标注
- 与真实飞行照片分开管理

### 管理功能
- **照片审核**：通过/拒绝照片，支持批量操作
- **用户管理**：用户信息管理、封号功能
- **申诉处理**：处理被拒绝照片的申诉
- **精选管理**：管理首页展示的精选照片
- **反馈管理**：用户反馈和评分系统

## 技术栈

- **后端**：PHP 8.1+
- **数据库**：MySQL 8.0+
- **Web服务器**：Nginx
- **前端**：Bootstrap 5, HTML5, CSS3, JavaScript
- **图片处理**：GD 扩展

## 安装部署

### 环境要求
- PHP 8.1 或更高版本
- MySQL 8.0 或更高版本
- Nginx 或 Apache
- PHP 扩展：PDO, GD, mbstring, openssl

### 安装步骤

1. **克隆代码到网站目录**
   ```bash
   cd /var/www/html
   # 代码已在 airplanes 目录中
   ```

2. **设置目录权限**
   ```bash
   chmod -R 755 /var/www/html/airplanes
   chmod -R 777 /var/www/html/airplanes/uploads
   mkdir -p /var/www/html/airplanes/uploads/thumbnails
   chmod -R 777 /var/www/html/airplanes/uploads/thumbnails
   ```

3. **配置 Nginx**
   ```bash
   cp /var/www/html/airplanes/nginx.conf /etc/nginx/sites-available/yhphotos
   ln -s /etc/nginx/sites-available/yhphotos /etc/nginx/sites-enabled/
   nginx -t
   systemctl oad nginx
   ```

4. **运行安装向导**
   - 访问 `http://your-domain/airplanes/install.php`
   - 填写数据库配置信息
   - 完成安装

5. **删除安装文件（重要）**
   ```bash
   rm /var/www/html/airplanes/install.php
   ```

### 默认管理员账户
- **用户名**：admin
- **密码**：admin123
- **邮箱**：admin@yhphotos.top

**⚠️ 安装后请立即修改管理员密码！**

## 目录结构

```
airplanes/
├── admin/                  # 管理后台
│   ├── index.php          # 控制台首页
│   ├── moderate-photos.php # 照片审核
│   └── ...
├── api/                   # API 接口
│   ├── like-photo.php     # 点赞功能
│   ├── download-photo.php # 下载统计
│   └── ...
├── auth/                  # 用户认证
│   ├── login.php          # 登录
│   ├── register.php       # 注册
│   ├── verify.php         # 邮箱验证
│   └── logout.php         # 退出登录
├── config/                # 配置文件
│   ├── config.php         # 主配置
│   └── database.php       # 数据库配置
├── database/              # 数据库文件
│   └── schema.sql         # 数据库结构
├── feedback/              # 反馈系统
│   └── index.php
├── gallery/               # 照片图库
│   └── index.php
├── includes/              # 公共文件
│   ├── header.php         # 页面头部
│   ├── footer.php         # 页面底部
│   └── image-processor.php # 图片处理
├── photo/                 # 照片详情
│   └── detail.php
├── profile/               # 用户主页
│   └── user.php
├── simulation/            # 模拟飞行专区
│   ├── index.php          # 模拟飞行首页
│   ├── gallery.php        # 模拟飞行图库
│   ├── upload.php         # 模拟飞行上传
│   └── detail.php         # 模拟飞行详情
├── upload/                # 照片上传
│   ├── index.php          # 上传页面
│   └── my-photos.php      # 我的照片
├── uploads/               # 上传文件目录
│   └── thumbnails/        # 缩略图目录
├── index.php              # 网站首页
├── nginx.conf             # Nginx 配置示例
└── README.md              # 说明文档
```

## 使用说明

### 用户功能
1. **注册账户**：填写用户名、邮箱、显示名称
2. **邮箱验证**：注册后需验证邮箱才能使用
3. **上传照片**：支持真实飞行和模拟飞行两个分区
4. **填写信息**：详细的飞机信息、拍摄地点等
5. **等待审核**：上传后等待管理员审核
6. **查看状态**：在"我的照片"中查看审核状态
7. **申诉功能**：对拒绝的照片可以提交申诉

### 管理员功能
1. **照片审核**：审核用户上传的照片
2. **用户管理**：管理用户账户，支持封号
3. **精选管理**：设置首页展示的精选照片
4. **申诉处理**：处理用户提交的申诉
5. **反馈查看**：查看用户反馈和建议

### 照片分类
- **商用航空**：民航客机等
- **军用航空**：军用飞机
- **通用航空**：私人飞机、公务机等
- **直升机**：各类直升机
- **货运航空**：货运飞机
- **经典机型**：老式飞机
- **机场设施**：机场相关照片

### 照片类型
- **起飞**：飞机起飞阶段
- **降落**：飞机降落阶段
- **滑行**：地面滑行
- **停机**：停机坪照片
- **客舱**：客舱内部
- **驾驶舱**：驾驶舱照片
- **外观**：飞机外观

## 配置说明

### 主要配置项（config/config.php）
- `SITE_NAME`：网站名称
- `BASE_URL`：网站基础路径
- `UPLOAD_PATH`：上传文件路径
- `MAX_FILE_SIZE`：最大文件大小限制
- `ADMIN_EMAIL`：管理员邮箱

### 邮件配置
默认使用 PHP 的 mail() 函数发送邮件。生产环境建议使用 SMTP：

```php
// 在 config.php 中配置 SMTP
define('SMTP_HOST', 'your-smtp-host');
define('SMTP_PORT', 587);
define('SMTP_USERNAME', 'your-email@domain.com');
define('SMTP_PASSWORD', 'your-password');
```

## 安全建议

1. **定期更新**：保持 PHP 和 MySQL 版本更新
2. **备份数据**：定期备份数据库和上传文件
3. **权限控制**：严格控制文件和目录权限
4. **HTTPS**：生产环境使用 SSL 证书
5. **防火墙**：配置防火墙规则
6. **监控日志**：定期检查错误和访问日志

## 故障排除

### 常见问题

1. **无法上传图片**
   - 检查 uploads 目录权限
   - 检查 PHP upload_max_filesize 设置
   - 检查 Nginx client_max_body_size 设置

2. **数据库连接失败**
   - 检查数据库配置信息
   - 确认 MySQL 服务正在运行
   - 检查数据库用户权限

3. **邮件发送失败**
   - 检查 PHP mail() 函数是否可用
   - 配置 SMTP 服务器
   - 检查邮件服务器设置

4. **图片水印不显示**
   - 确认 GD 扩展已安装
   - 检查图片处理权限
   - 查看错误日志

### 日志位置
- **Nginx 错误日志**：`/var/log/nginx/yhphotos_error.log`
- **Nginx 访问日志**：`/var/log/nginx/yhphotos_access.log`
- **PHP 错误日志**：`/var/log/php/error.log`

## 贡献

欢迎提交 Issue 和 Pull Request 来改进项目。

## 许可证

本项目采用 MIT 许可证，详见 LICENSE 文件。

## 联系我们

- **项目地址**：GitHub Repository
- **问题报告**：GitHub Issues
- **邮箱联系**：admin@yhphotos.top

---

**感谢使用 YHPhotos！** 🛩️



