---
layout: post
title: SSH를 이용해서 톰캣을 실행 하는법
---

##How to restart tomcat using ansible ?

Ansible에서 command 기능으로 원격노드의 톰캣 실행 스크립트를 실행하면 실질적으로 tomcat이 실행되지 않는다.

tomcat은 터미널 세션이 끊기면, 스레드가 중단됨에 따라 tomcat 서버도 종료되기 때문이다.

리눅스의 nohup ( 로그아웃 하여 터미널을 빠져나가도 실행중인 프로그램이 종료되지 않고 계속 수행될 수 있게 하는 명령 ) 명령어를 이용해서 스크립트를 수정하면 된다.

내가 수정한 스크립트는 tomcat/bin/startup.sh 스크립트에서 톰캣을 시작하는 명령을 아래와 같이 수정하였다. (nohup 추가 )

To start tomcat to remote server using andible, you should edit the script to start tomcat to remote node. as below ~

~~~shell
exec nohup “$PRGDIR”/”$EXECUTABLE” start “$@”
~~~

>위 사항은 ssh를 이용해서 tomcat을 시작할 때도 유효하다. 톰캣 실행 스크립트를 데몬 스레드로 돌려야 한다. 