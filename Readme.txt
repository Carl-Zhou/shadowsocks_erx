
shadowsocks for EdgeRouter X

��װ:
1.����shadowsocks_erx-master.zip����ѹ
2.��winscp�ѽ�ѹ�����ļ�copy��/tmpĿ¼
3.����·��CLI������沢��½��Ȼ��ִ��: sudo bash install.sh
4.������ʾ����shadowsocks������Ϣ��һ��ֻ��Ҫ�����������ַ���˿ڡ����룬����ѡ�����ֱ�ӻس�ʹ��Ĭ��ѡ�

ע��:
1.�����������Զ�������ͨ��ipset�Թ���IP���а�����������IP���ᷭǽ���ʣ�ֻ�й�����������shadowsocksͨ����ǽ
2.ֻ�ܶ�TCP������ǽ��UDPֻ��DNS����ͨ��ss-tunnel��ǽ
3.1080�˿ڿ�����Ϊsocks5��ǽ����ʹ��
4.�ļ������/configĿ¼����Ϊ���Ŀ¼�������õ�ʱ��ᱻһ�𱸷ݣ�����ϵͳ����Ҳ����ɾ��
5.shadowsocks�汾:v2.4.4, chinadns�汾:v1.3.2���������汾Ŀǰ�����ȶ�������û���������ڿ��ǻ�����
6.EdgeRouter X EdgeOS v1.8.5,v1.9.0����ͨ��
7.�������ͣshadowsocks������sudo /etc/init.d/shadowsocks stop
8.��������������sudo /etc/init.d/shadowsocks start
9.shadowsocksҪ����chinadns������ű�:/etc/init.d/chinadns����Ҫ���׹ر�


�������������(����ISP DNS����Ϊ114.114.114.114):
/config/shadowsocks/bin/ss-local -u -l 1080 -c /config/shadowsocks/conf/shadowsocks.json -f /var/run/ss-local.pid
/config/shadowsocks/bin/ss-tunnel -u -c /config/shadowsocks/conf/shadowsocks.json -l 5302 -L 8.8.8.8:53 -f /var/run/ss-tunnel.pid
/config/shadowsocks/bin/ss-redir -u -l 1081 -c /config/shadowsocks/conf/shadowsocks.json -f /var/run/ss-redir.pid
/config/shadowsocks/bin/chinadns /var/run/chinadns.pid -p 5301 -s 114.114.114.114,127.0.0.1:5302 -c /config/shadowsocks/conf/chinadns_chnroute.txt

DNS��������
chinadns    ������������һ������DNS��һ������DNS
dnsmasq  ->    chinadns    (����IP)->    ss-tunnel   -> ss-server -> dns-server:ok
			   (����IP)->    114.114.114.114:ok

