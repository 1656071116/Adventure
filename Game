#include<bits/stdc++.h>
#include<windows.h>
#include<winuser.h>
#include<conio.h>
#define tab srand(unsigned(time(NULL)))
#define set SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE),FOREGROUND_INTENSITY |FOREGROUND_RED | FOREGROUND_GREEN | FOREGROUND_BLUE)
#define clear system("cls")
#define random(l,r) l+rand()%(r-l+1)
#define down(VK_NONAME) ((GetAsyncKeyState(VK_NONAME) & 0x8000) ? 1:0)
using namespace std;
string s[11]= {"\0","1.开始","2.游戏介绍","3.设置","4.更新日志","5.退出"};
bool unlock[101];
int cooldown[101];
string skill[101]= {"\0","\0","回血","闪电","抗性【被动】","防毒","闪避【被动】","吸血","力量","爆破"};
int x=1,Exhp,strength=0,mana=100;
void print(string u,int t) {
	for(int i=0; i<u.length(); i++) {
		if(u[i]=='\\') {
			putchar('\n');
			Sleep(t);
			continue;
		}
		putchar(u[i]);
		Sleep(t);
	}
}
inline void red(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_RED);
	print(u,t);
	set;
}
inline void blue(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_BLUE);
	print(u,t);
	set;
}
inline void green(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_GREEN);
	print(u,t);
	set;
}
inline void yellow(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_RED | FOREGROUND_GREEN);
	print(u,t);
	set;
}
inline void cyan(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_GREEN | FOREGROUND_BLUE);
	print(u,t);
	set;
}
inline void pink(string u,int t) {
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_INTENSITY | FOREGROUND_RED | FOREGROUND_BLUE);
	print(u,t);
	set;
}
void backspace(int,int);
void menu();
void load(string,int);
void figure(string,int,int);
int pau=20;
int dx=29,dy=47;
int rx=2,ry=2;
string c[5]= {"\0","█","M ","R ","I "};
struct map_game {
	int ch;//编号
	int color;//颜色
	int pd;//是否为空格
} mapn[33][101];
inline void new_map() {//生成地图的四周
	for (int i=1; i<=dx+2; i++) {
		mapn[i][1].ch=1;
		mapn[i][1].color=1;
		mapn[i][1].pd=0;
		mapn[i][dy+2].ch=1;
		mapn[i][dy+2].color=1;
		mapn[i][dy+2].pd=0;
	}
	for (int i=1; i<=dy+2; i++) {
		mapn[1][i].ch=1;
		mapn[1][i].color=1;
		mapn[1][i].pd=0;
		mapn[dx+2][i].ch=1;
		mapn[dx+2][i].color=1;
		mapn[dx+2][i].pd=0;
	}
	for (int i=2; i<=dx+1; i++) {
		for (int j=2; j<=dy+1; j++) {
			mapn[i][j].pd=1;
		}
	}
}
inline void map_print() {//输出地图
	clear;
	for (int i=1; i<=dx+2; i++) {
		for (int j=1; j<=dy+2; j++) {
			if(mapn[i][j].pd) {
				putchar(32);
				putchar(32);
			} else {
				if (mapn[i][j].color==1) {
					print(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==2) {
					red(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==3) {
					blue(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==4) {
					green(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==5) {
					yellow(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==6) {
					cyan(c[mapn[i][j].ch],0);
				} else if(mapn[i][j].color==7) {
					pink(c[mapn[i][j].ch],0);
				}
			}
		}
		putchar('\n');
	}
}
inline void new_guai() {
	rx=2;
	ry=2;
	mapn[rx][ry].pd=0;
	mapn[rx][ry].ch=3;
	mapn[rx][ry].color=0;
	int num=random(15,23);
	for (int i=1; i<=num; i++) {
x:
		int gx=random(2,dx+1),gy=random(2,dy+1);
		if(gx==rx&&gy==ry) goto x;
		if(!mapn[gx][gy].pd) goto x;
		mapn[gx][gy].pd=0;
		mapn[gx][gy].ch=2;
		mapn[gx][gy].color=1;
	}
	num=random(7,12);
	for (int i=1; i<=num; i++) {
y:
		int gx=random(2,dx+1),gy=random(2,dy+1);
		if(gx==rx&&gy==ry) goto y;
		if(!mapn[gx][gy].pd) goto y;
		mapn[gx][gy].pd=0;
		mapn[gx][gy].ch=2;
		mapn[gx][gy].color=4;
	}
	num=random(3,8);
	for (int i=1; i<=num; i++) {
xy:
		int gx=random(2,dx+1),gy=random(2,dy+1);
		if(gx==rx&&gy==ry) goto xy;
		if(!mapn[gx][gy].pd) goto xy;
		mapn[gx][gy].pd=0;
		mapn[gx][gy].ch=2;
		mapn[gx][gy].color=6;
	}
}
inline void new_item() {
	rx=2;
	ry=2;
	mapn[rx][ry].pd=0;
	mapn[rx][ry].ch=3;
	mapn[rx][ry].color=5;
	int num=random(5,10);
	for (int i=1; i<=num; i++) {
y:
		int gx=random(2,dx+1),gy=random(2,dy+1);
		if(gx==rx&&gy==ry) goto y;
		if(!mapn[gx][gy].pd) goto y;
		mapn[gx][gy].pd=0;
		mapn[gx][gy].ch=4;
		mapn[gx][gy].color=2;
	}
}
inline void pick() {
	clear;
	SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,1000});
	int ski;
	ski=random(2,9);
	red("您捡起了【",pau);
	cout<<skill[ski];
	red("】\\",pau);
	unlock[ski]=true;
	red("按【R】确定\\",pau);
	char d;
Y:
	d=getch();
	if(!(d=='R' || d=='r')) goto Y;
	SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,32});
	return;
}
inline void video(int harder,int color) {
	clear;
	SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,1000});
	int mHp=150+20*Exhp,dHp=random(max(100,int(100*log2(harder-1))),int(log2(100*harder))),stage=0;
	print(" O      OO\\",0);
	print("/|     /||----| \\",0);
	print("/|      | |   | |\\",0);
	if(color==4) yellow("你     怪 level 2\\",0);
	else if(color==6) yellow("你     怪 level 3\\",0);
	else if(color==-1) yellow("你     怪 level 4\\",0);
	else yellow("你     怪 level 1\\",0);
	if(color==4) dHp+=35;
	if(color==6) dHp+=120;
	print("己方血量：",pau);
	cout<<mHp;
	print(" 敌方血量：",pau);
	cout<<dHp<<endl;
	int t=0,poison=0,unpoi=0,opski,streng=0,J=pau;
	while (mHp>0 && dHp>0) {
		pau=0;
		stage++;
		cyan ("第",pau);
		printf ("%d",stage);
		cyan ("回合\\",pau);
		if(mana<100) mana+=5;
		cyan("mana:",pau);cout<<mana;
		cyan("  目前可用:\\",pau);
		if(unlock[4]) green("被动:抗性 减少20\%伤害\\",pau);
		if(unlock[6]) green("被动:闪避 有20\%几率闪避\\",pau);
		green("  【Q】射击 使敌方血量减10\\",pau);
		green("  【T】mana 回复自己mana值20点\\",pau);
		if(cooldown[1]==0 && mana>=15) green("  【F】冰冻 使敌方两个回合无法使出技能(CD:5,mana:15)\\",pau);
		if(unlock[2] && cooldown[2]==0 && mana>=40) green("  【G】回血 血量+30(CD:8,mana:40)\\",pau);
		if(unlock[3] && cooldown[3]==0 && mana>=25) green("  【P】闪电 使敌方血量减5，眩晕一回合(CD:5,mana:25)\\",pau);
		//unlock[4] 是被动
		if(unlock[5] && cooldown[5]==0 && mana>=20) green("  【K】防毒 防止两回合中毒(CD:5,mana:20)\\",pau);
		//unlock[6]是被动
		if(unlock[7] && cooldown[7]==0 && mana>=25) green("  【X】吸血 使敌方血量减5,自身血量加5(CD:5,mana:20)\\",pau);
		if(unlock[8] && cooldown[8]==0 && mana>=40) green("  【L】力量 三回合内对射击力量加成100\% (CD:6,mana:40)\\",pau);
		if(unlock[9] && cooldown[9]==0 && mana>=45) green("  【N】爆破 使敌方血量减25，眩晕三回合(CD:11,mana:45)\\",pau);
		if (poison) {
			green("您被对方的 毒药 毒中了 血量减",pau);
			int pr;
			pr=random(1,5);
			if(!unlock[4]) cout<<5<<endl;
			else cout<<4<<endl;
			if(pr==5) {
				green("暴击!血量减",pau);
				if(!unlock[4]) cout<<10<<endl;
				else cout<<8<<endl;
			}
			poison--;
			if (poison) {
				green("您被毒中还剩",pau);
				printf ("%d",poison);
				green ("天\\",pau);
				if(unlock[6]) {
					int pre;
					pre=random(1,5);
					if(pre==5) {
						print("闪避!\\",pau);
						if(!unlock[4]) mHp+=5;
						else mHp+=4;
						if(pr==5) {
							if(!unlock[4]) mHp+=5;
							else mHp+=4;
						}
					}
				}
				if(!unlock[4]) mHp-=5;
				else mHp-=4;
				if(pr==5) {
					if(!unlock[4]) mHp-=5;
					else mHp-=4;
				}
			}
			if(unpoi) {
				if(!unlock[4]) mHp+=5;
				else mHp+=4;
				if(pr==5) {
					if(!unlock[4]) mHp+=5;
					else mHp+=4;
				}
				green("由于防毒免受伤害\\",pau);
			}
			if(poison==0) {
				green ("您中毒结束了\\",pau);
			}
		}
		if (t) {
			green("对方不可行动还剩",pau);
			printf ("%d",t);
			green ("天\\",pau);
		}
		while (1) {
			pau=J;
T:
			if (down('Q') || down('q')) {
				dHp-=10*(1+0.2*strength);
				cyan("您使用了【Q】射击 使敌方血量减",pau);
				cout<<10*(1+0.2*strength)<<endl;
				if(streng) {
					cyan("力量暴击!血量减",pau);
					cout<<20*(1+0.2*strength)<<endl;
					dHp-=10*(1+0.2*strength);
				}
				goto X;
			}
			if (down('T') || down('t')) {
				if(mana==100){
					red("您的mana已经回满,请尝试使用其他技能\\",pau);
					goto T;
				}
				cyan("您使用了【T】mana 回复mana20点\\",pau);
				mana+=20;
				if(mana>100) mana=100;
				goto X;
			}
			if (down('F') || down('f')) {
				if(cooldown[1]==0 && mana>=15) {
					t+=2;
					cyan("您使用了【F】冰冻 对方无法行动还剩",pau);
					printf("%d",t);
					cyan("天\\",pau);
					cooldown[1]+=5;
					mana-=15; 
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[2] &&(down('G') || down('g'))) {
				if(cooldown[2]==0 && mana>=40) {
					cyan("您使用了【G】回血 血量+30\\",pau);
					mHp+=30;
					cooldown[2]+=8;
					mana-=40;
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[3] &&(down('P') || down('p'))) {
				if(cooldown[3]==0 && mana>=25) {
					cyan("您使用了【P】闪电 使敌方血量减5 ",pau);
					++t;
					dHp-=5;
					cyan("对方无法行动还剩",pau);
					printf("%d",t);
					cyan("天\\",pau);
					mana-=25;
					cooldown[3]+=5;
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[5] &&(down('K') || down('k'))) {
				if(cooldown[5]==0 && mana>=20) {
					cyan("您使用了【K】防毒 防止两回合中毒\\",pau);
					unpoi+=2;
					cooldown[5]+=5;
					mana-=20;
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[7] &&(down('X') || down('x'))) {
				if(cooldown[7]==0 && mana>=20) {
					cyan("您使用了【X】吸血 使敌方血量减5,自身血量加5\\",pau);
					mHp+=5;
					dHp-=5;
					cooldown[7]+=5;
					mana-=20; 
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[8] &&(down('L') || down('l'))) {
				if(cooldown[8]==0 && mana>=40) {
					cyan("您使用了【L】力量 力量加成100\%\\",pau);
					streng+=3;
					cooldown[8]+=6;
					mana-=40;
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
			if (unlock[9] &&(down('N') || down('n'))) {
				if(cooldown[9]==0 && mana>=45) {
					cyan("您使用了【N】爆破 使敌方血量减25，眩晕三回合\\",pau);
					dHp-=25;
					t+=3;
					cooldown[9]+=11;
					mana-=45;
					goto X;
				} else {
					red("您现在无法使用此技能\\",pau);
					goto T;
				}
			}
		}
X:
		if (dHp<=0||mHp<=0) goto M;
		if (t) goto M;
		opski=random(1,3);
		if (opski<3) {
			cyan("敌方使用了 咆哮 使我方血量减",pau);
			int pr;
			pr=random(1,5);
			if(pr<=4) {
				if(!unlock[4]) cout<<10<<endl;
				else cout<<8<<endl;
				if(!unlock[4]) mHp-=10;
				else mHp-=8;
			} else {
				if(!unlock[4]) cout<<10<<endl;
				else cout<<8<<endl;
				cyan("暴击!血量减",pau);
				if(!unlock[4]) cout<<20<<endl;
				else cout<<16<<endl;
				if(!unlock[4]) mHp-=20;
				else mHp-=16;
			}
			if(unlock[6]) {
				int pre;
				pre=random(1,5);
				if(pre==5) {
					print("闪避!\\",pau);
					if(!unlock[4]) mHp+=10;
					else mHp+=8;
				}
			}
		}
		if (opski==3) {
			cyan("敌方使用了 毒药 使我方在2个回合内每回合减5\\",pau);
			poison+=2;
		}
M:
		red ("我方血量：",pau);
		printf ("%d\n",max(mHp,0));
		red ("敌方血量：",pau);
		printf ("%d\n\n",max(dHp,0));
		for(int i=1; i<=100; i++) if(cooldown[i]>0) --cooldown[i];
		if(unpoi>0) --unpoi;
		if(t>0) --t;
		if(streng>0) --streng;
	}
	if (dHp<=0) {
		blue ("您赢得了胜利！\\",pau);
		int b;
		b=random(1,10);
		if(b<=2) {
			blue("掉落物:【血量加成】 血量上限+20\\",pau);
			Exhp+=1;
		} else if(b>=3 && b<=5) {
			blue("掉落物:【力量加成】 射击伤害+20%\\",pau);
			++strength;
		} else blue("掉落物:无\\",pau);
		SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,32});
		system("pause");
	} else {
		blue ("您输了！\\",pau);
		Sleep(500);
		SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,32});
		system("pause");
		menu();
	}
	return;
}
inline void move() {//移动
	int p=rx,q=ry;
	bool moved=0;
	if(down('W')||down('w')) {
		if (rx>2) {
			rx--;
			moved=1;
		}
	}
	if(down('S')||down('s')) {
		if (rx<=dx) {
			rx++;
			moved=1;
		}
	}
	if(down('A')||down('a')) {
		if (ry>2) {
			ry--;
			moved=1;
		}
	}
	if(down('D')||down('d')) {
		if (ry<=dy) {
			ry++;
			moved=1;
		}
	}
	if(down('E')||down('e')) {
		menu();
	}
	if (moved) {
		if (mapn[rx][ry].ch==2) {
			video(int(1+Exhp),mapn[rx][ry].color);
		}
		if (mapn[rx][ry].ch==4) {
			int pr;
			pr=random(1,10);
		    if(pr<5) video(random(2,3)+1+Exhp,-1);
		    pick();
		}
		mapn[p][q].pd=1;
		mapn[rx][ry].pd=0;
		mapn[rx][ry].ch=3;
		mapn[rx][ry].color=5;
		map_print();
	}
	Sleep(125);
}
inline void start() {//开始游戏
	clear;
	new_map();
	new_guai();
	new_item();
	map_print();
	while (1) {
		move();
	}
	Sleep(1000);
	return;
}
int main() {
	tab;
	system("mode con cols=100 lines=32");
	system("title Adventure");
	SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), {100,32});
	load("By wjh_ and 553032651yyj",0);
	menu();
}
//w 119
//a 97
//s 115
//d 100
//enter 13
void backspace(int t,int u) {
	for(int i=1; i<=t; i++) {
		cout<<' ';
		Sleep(u);
	}
}
void figure(string u,int mode,int t) {
	backspace((100-u.length())/2,t);
	if(mode==1) print(u,t);
	if(mode==2) green(u,t);
}
void load(string logo,int mode) {
	for(int i=1; i<=20; i++) {
		clear;
		print("\\\\\\\\\\\\\\\\\\\\\\\\",0);
		figure("加载中...\\",1,0);
		backspace(30,0);
		for(int j=1; j<=i; j++) {
			green("▄",0);
		}
		for(int j=1; j<=20-i; j++) {
			print("▄",0);
		}
		print("\\",0);
		figure(logo,1,0);
		if(mode==1) {
			print("\\",0);
			figure("Tip:按E键可返回菜单",1,0);
			if(down('e') || down('E')) menu();
		}
		Sleep(50);
	}
	return;
}
void menu() {
//	memset(unlock,false,sizeof(unlock));
	x=1;
	int a;
B:
	while(1) {
		clear;
		figure("请点击w,s控制上下选择,Enter确认.",1,0);
		print("\\\\\\\\\\\\\\\\",0);
		figure("Adventure Game",2,0);
		print("\\\\\\\\\\\\",0);
		for(int i=1; i<=5; i++) {
			if(x==i) {
				string u=s[x];
				u='>'+u+'<';
				figure(u,2,0);
			} else figure(s[i],1,0);
			print("\\\\",0);
		}
		a=getch();
		if(a==119 && x>1) --x;
		if(a==115 && x<5) ++x;
		if(a==13) break;
	}
	switch(x) {
		case 1:
			load("\0",1),start();
		case 2:
			return;
		case 3:
			return;
		case 4:
			clear;
			green("v0.0.1 加入基本设施,加入9个技能,简化代码\\",10);
			green("v0.0.2 对部分技能进行微调,怪物技能有20\%几率暴击\\",10);
			green("v0.0.3 加入mana设定\\",10);
			system("pause");
			goto B;
			break;
		case 5:
			return;
		default:
			;
	}
}
