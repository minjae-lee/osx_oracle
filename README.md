osx_oracle
==========

## 목표

OSX 환경에서 Python으로 oracle에 접근하는 방법을 제공

## 동기

OSX 환경에서 Python으로 oracle에 접근하기 위해서는 몇가지 방법이 존재를 하는데, 각각 다음과 같은 문제들이 발생한다.

* cx_oracle: OSX lion이후 버전서 부터 동작을 하지 않음
* JayDeBeApi: 같은 JNI를 사용하는 pylucene과 충돌을 일으킨다.
* pyodbc: 유료로 파는 odbc driver를 사용해야 하며, odbc driver들이 JNI를 사용하기 때문여, 역시 pylucene과 충돌을 일으킨다.
* mxodbc connect: 유료이기는 하지만 pylucene과 총돌은 일으키지 않는다.

osx_oracle은 무료이면서 pylucene과 함께 동작을 할 수 있는 oracle 접근 방법을 제공하는 것을 목표로 한다.

## 기본 접근 방법

JayDeBeApi를 사용하되, pylucene과 충돌을 일으키지 않게 만든다. JayDeBeApi가 pylucene과 충돌을 일으키는 이유는 둘다 JNI를 통해 JVM에 접근을 하기 때문이다. 만약 이 둘을 서로 다른 process에서 동작을 시킨 다면, JVM간에 충돌이 발생하지 않는다.
