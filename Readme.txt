
shadowsocks for EdgeRouter X

��װ:
1.����shadowsocks_erx-master.zip����ѹ
2.��winscp�ѽ�ѹ�������ļ�copy��/tmpĿ¼
3.����·��CLI������沢��½��Ȼ��ִ��: 
cd /tmp
sudo bash install.sh
4.������ʾ����shadowsocks������Ϣ��һ��ֻ��Ҫ�����������ַ���˿ڡ����룬����ѡ�����ֱ�ӻس�ʹ��Ĭ��ѡ�

ע��:
1.�����������Զ�������ͨ��ipset�Թ���IP���а�����������IP���ᷭǽ���ʣ�ֻ�й�����������shadowsocksͨ����ǽ
2.ֻ�ܶ�TCP������ǽ
3.������վDNS��shadowsocks��������תʹ��TCP����8.8.8.8����ֹ��Ⱦ����������ʹ�ù���DNS����������Ӱ��CDN����
4.1080�˿ڿ�����Ϊsocks5��ǽ����ʹ��
5.�ļ������/configĿ¼����Ϊ���Ŀ¼�������õ�ʱ��ᱻһ�𱸷ݣ�����ϵͳ����Ҳ����ɾ��
6.shadowsocks�汾:v2.5.6, chinadns�汾:v1.3.2(�޸İ�)��pdnsd�汾:v1.2.9
7.EdgeRouter X EdgeOS v1.8.5,v1.9.0����ͨ��
8.�������ͣshadowsocks������sudo /etc/init.d/shadowsocks stop
9.��������������sudo /etc/init.d/shadowsocks start


DNS��������
chinadns    ������������һ������DNS��һ������DNS
dnsmasq  ->    chinadns    (����IP)->    pdnsd   -> ss-server -> dns-server:ok
			   (����IP)->    114.114.114.114:ok

chinadns���ߺܾ�û�и��¹��ˣ������м���bug���ᵼ����Щͬʱ�й��ڹ���CDN�����������������IP��������ʹ�õ�chinadns���޸������bug���Ż��˲�������µĽ����ٶȡ�
ss��ǽ����Ŀǰ�����׳�����ľ���DNS����Ⱦ������ļ��θ��¼����������DNS����Ŀǰ�汾�������ұȽ������ˡ�
