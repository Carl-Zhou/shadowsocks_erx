
shadowsocks for EdgeRouter X

��װ:
1.�޸�/config/shadowsocks/conf/shadowsocks.json��������
2.�ѳ�Readme��������ļ����Ƶ���ӦĿ¼�ṹ
3./etc/dnsmasq.conf�����һ���Լ�ISP��DNS���߹���DNS
server=114.114.114.114
3.chmod��ӿ�ִ��Ȩ�޲�����
chmod +x /etc/init.d/shadowsocks
chmod +x /etc/init.d/chinadns
/etc/init.d/shadowsocks start
/etc/init.d/chinadns start

ע��:
1.�����������Զ�������ͨ��ipset�Թ���IP���а�����������ǽ���ʣ�ֻ�й�����������shadowsocksͨ����ǽ
2.ֻ�ܶ�TCP������ǽ��UDPֻ��DNS����ͨ��ss-tunnel��ǽ
3.1080�˿ڿ�����Ϊsocks5��ǽ����ʹ��
4.�ļ������/configĿ¼����Ϊ���Ŀ¼�������õ�ʱ��ᱻһ�𱸷ݣ�����ϵͳ����Ҳ����ɾ��

�������������(����ISP DNS����Ϊ114.114.114.114):
/config/shadowsocks/bin/ss-local -u -l 1080 -c /config/shadowsocks/conf/shadowsocks.json -f /var/run/ss-local.pid
/config/shadowsocks/bin/ss-tunnel -u -c /config/shadowsocks/conf/shadowsocks.json -l 5302 -L 8.8.8.8:53 -f /var/run/ss-tunnel.pid
/config/shadowsocks/bin/ss-redir -u -l 1081 -c /config/shadowsocks/conf/shadowsocks.json -f /var/run/ss-redir.pid
/config/shadowsocks/bin/chinadns /var/run/chinadns.pid -p 5301 -s 114.114.114.114,127.0.0.1:5302 -c /config/shadowsocks/conf/chinadns_chnroute.txt

DNS��������
chinadns    ������������һ������DNS��һ������DNS
dnsmasq  ->    chinadns    (����IP)->    ss-tunnel   -> ss-server -> dns-server:ok
			   (����IP)->    114.114.114.114:ok
