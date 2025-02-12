# 移动设备怎样定位
## 现象
### 没有GPS接收器的设备可以定位

- 云翼的iPad 1代 Wifi版（型号MD292CH），在接入公司wifi的情况下，可在地图软件上定位到“我的位置”
- 五福的三星手机，不开GPS模块，但接入了Wifi和移动运营商，可在百度地图上定位到“我的位置”

### 不接入网络可以定位

- 吴笑的iPhone 4S，关闭无线网和蜂窝数据（包括2G，3G），可以定位
- 吴笑的车载导航，只有GPS接收器，没有任何网络接入，可以定位导航

## 定位原理（先说理想空间里的几何模型，通信和经纬度后补）
### 仅依靠GPS定位
GPS接收器与卫星1通信，获得与卫星1（记为Sat_1）的距离（记为Dist_1）
GPS接收器与卫星2通信，获得与卫星2（记为Sat_2）的距离（记为Dist_2）

分别以Sat_1, Sat_2为圆心，Dist_1, Dist_2为半径，画一个球，两球相交得一个空心圆，接收器在这个空心圆上某一点。

如果再有第三颗GPS卫星，同理画一个球，运气好的话，此球与空心圆有一个交点（相切），此时三颗星就可定位了。 如果不相切，球与圆圈有两个交点，排除一个不在地球表面的（可以理解为地球表面作为第四个球参与确定交点），剩下那个点即为接收机所在位置。

（注：之前，我想的是：运气不好的话三颗星只能画三个球面，有两个交点，这就需要第四颗卫星来画第四个球了。后来查了资料，才知道这不对，再加上地球本身第四个球面，已经可以唯一确定接收机的位置了）

### 仅依靠WIFI热点定位

wifi的有效距离比较有限，可以不考虑地球曲面的影响，简单认为wifi热点跟要定位的移动终端在同一个平面上。把上面GPS定位原理的圆球改为圆圈，在水平面画圆圈。理论上，最好的情况下，两个wifi热点可定位成功（两个圆正好相切），不在同一直线上的三个wifi热点一定能找到唯一交点，定位成功。
### 仅依靠WIFI热点定位（MAC地址）
wifi接入时，google或者某些国内大厂（在后台各种收集用户信息）可以通过路由器的mac地址（而不是宽带拨号获得的动态IP地址）来匹配地理位置
您能在此处看到 http://www.ip2location.com/html5geolocationapi.aspx

### 仅依靠GSM基站定位
与wifi定位相同

### 辅助定位
AGPS
