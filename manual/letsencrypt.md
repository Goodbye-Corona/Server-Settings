1. system update & install packages
```
apt update && apt upgrade -y && apt install certbot python3-certbot-nginx -y
```
2. Install SSL
```
certbot --nginx
```
3. Auto-renew
```
현재 설정된 crontab 내용 출력
$ sudo crontab -l
```
    crontab 내용 입력(편집). nano 선택 후 수정
    $ sudo crontab -e

```
# m h  dom mon dow   command

# 격월 1일 새벽4시에 $ certbot renew 수행하고, 갱신에 성공하면 nginx 다시시작
0 4 1 */2 * sudo /usr/bin/certbot renew --renew-hook "sudo systemctl restart nginx"
```
참고: 인증서 모의 갱신

    sudo certbot renew --dry-run

