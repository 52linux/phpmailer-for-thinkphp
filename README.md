# phpmailer-for-thinkphp

放入TP5.0的extend目录
调用方法
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;
$mail = new PHPMailer(true);
try {
    // 服务器设置
    $mail->SMTPDebug = 2;                                    // 开启Debug
    $mail->isSMTP();                                        // 使用SMTP
    $mail->Host = 'smtp.qq.com';                        // 服务器地址
    $mail->SMTPAuth = true;                                    // 开启SMTP验证
    $mail->Username = 'xxxxxx@qq.com';                // SMTP 用户名（你要使用的邮件发送账号）
    $mail->Password = 'xxxxxx';                                // SMTP 密码
    $mail->SMTPSecure = 'tls';                                // 开启TLS 可选
    $mail->Port = 587;                                        // 端口
    
    /* 
    $mail->SMTPSecure = 'ssl';                                // 开启TLS 可选
    $mail->Port = 462;                                        // 端口
    */
    
    // 收件人
    $mail->setFrom('admin@sandboxcn.com', 'SandBoxCn');            // 来自
    $mail->addAddress('23275429@qq.com', 'George.Haung');        // 添加一个收件人
    $mail->addAddress('23275429@qq.com');                        // 可以只传邮箱地址
    $mail->addReplyTo('admin@sandboxcn.com', 'SandBoxCn');        // 回复地址
    // $mail->addCC('cc@example.com');
    // $mail->addBCC('bcc@example.com');
    // 附件
    $mail->addAttachment('/var/tmp/file.tar.gz');                // 添加附件
    $mail->addAttachment('/tmp/image.jpg', 'new.jpg');            // 可以设定名字
    // 内容
    $mail->isHTML(true);                                        // 设置邮件格式为HTML
    $mail->Subject = '欢迎注册成为SandBoxCN的一员:)';
    $mail->Body    = '欢迎注册成为<b>SandBoxCN</b>的一员';
    $mail->AltBody = 'xxxxxx';
    $mail->send();
    echo '邮件发送成功。<br>';
} catch (Exception $e) {
    echo '邮件发送失败。<br>';
    echo 'Mailer Error: ' . $mail->ErrorInfo;
}
