keytool
===========
JDK 中 keytool 是用来管理密钥库,证书,公私钥的工具.

## 密钥生成与加密
生成公私钥

    # 将生成的密钥 key_name 存入 .my.certs 文件.结尾需要设置密码,表示以后使用该公私钥的口令.
    $ keytool -genkeypair -keystore .my.certs -alias key_name
    
导出公钥

    # 将.my.certs库中的key_name公钥导出到文件 young.cer
    $ keytool -exportcert -keystore .my.certs -alias key_name -file young.cer
    
对 .jar 文件进行加密

    $ jarsigner -keystore .my.certs yourfile.jar key_name
    # 如果文件不再.jar文件中使用命令加入
    $ jar cvf youfile.jar your-other-file

## 添加别人的公钥并验证文件
收到别人的公钥文件后查看,以此来核对是否是别人的公钥

    $ keytool -printcert -file young.cer
    
信任别人的公钥证书后,导入自己的密钥库

    $ keytool -importcert -keystore other.certs -alias other -file young.cer
    
获取文件和公钥后对文件进行验证

    # 验证成功输出  jar verified.
    $ jarsigner -verify -keystore other.certs yourfile.jar
