<<<<<<< Current (Your changes)
# qflow_second_verify
=======
# 短信二次验证页面

这是一个完整的短信验证前端页面，支持自动获取手机号、发送验证码、验证码验证以及验证成功后的自动跳转。

## 功能特性

- ✅ 自动获取用户手机号（接口1）
- ✅ 发送短信验证码（接口2）
- ✅ 验证码输入和验证
- ✅ 60秒倒计时防重复发送
- ✅ 验证成功后自动跳转
- ✅ 响应式设计，支持移动端
- ✅ 优雅的加载状态和错误处理

## 使用方法

### 1. URL参数配置跳转地址

页面支持通过URL参数传入跳转地址：

```
sms-verification.html?redirect=https://example.com/dashboard
sms-verification.html?redirectUrl=/admin/panel
```

支持的参数：
- `redirect`: 跳转URL
- `redirectUrl`: 跳转URL（备选参数名）

如果没有提供参数，默认跳转到 `/dashboard`

### 2. 接口配置

您需要配置以下两个API接口：

#### 接口1：获取手机号
```
GET /api/user/phone
```

响应格式：
```json
{
  "phone": "13800138000",
  "success": true
}
```

#### 接口2：发送验证码
```
POST /api/sms/send
```

请求格式：
```json
{
  "phone": "13800138000",
  "type": "verification"
}
```

响应格式：
```json
{
  "success": true,
  "message": "验证码已发送"
}
```

#### 接口3：验证验证码
```
POST /api/sms/verify
```

请求格式：
```json
{
  "phone": "13800138000",
  "code": "123456"
}
```

响应格式：
```json
{
  "success": true,
  "message": "验证成功"
}
```

### 3. 认证配置

如果您的API需要认证，请在代码中取消注释相关的Authorization头：

```javascript
headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer ' + localStorage.getItem('token')
}
```

### 4. 自定义样式

页面使用了现代化的渐变设计，您可以通过修改CSS变量来自定义颜色主题：

```css
:root {
    --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    --success-color: #28a745;
    --error-color: #dc3545;
}
```

## 使用示例

### 基本使用
```html
<a href="sms-verification.html?redirect=/dashboard">进行短信验证</a>
```

### 跳转到外部网站
```html
<a href="sms-verification.html?redirect=https://example.com/success">验证后跳转</a>
```

### JavaScript调用
```javascript
// 验证成功后跳转到指定页面
window.location.href = 'sms-verification.html?redirect=' + encodeURIComponent(targetUrl);
```

## 安全建议

1. **HTTPS**: 确保在生产环境中使用HTTPS
2. **CSRF保护**: 在API接口中实现CSRF保护
3. **频率限制**: 在后端实现发送验证码的频率限制
4. **验证码过期**: 设置验证码的有效期（建议5-10分钟）
5. **IP限制**: 可以考虑对同一IP的验证次数进行限制

## 浏览器兼容性

- Chrome 60+
- Firefox 55+
- Safari 12+
- Edge 79+

## 移动端优化

- 响应式设计，适配各种屏幕尺寸
- 数字键盘自动弹出
- 触摸友好的按钮尺寸
- 优化的视觉反馈
>>>>>>> Incoming (Background Agent changes)
