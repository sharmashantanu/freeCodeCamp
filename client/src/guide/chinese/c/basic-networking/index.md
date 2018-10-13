---
title: Basic Networking
localeTitle: 基础网络
---
## 基础网络

C中的基本网络主要涉及打开套接字并通过它们进行通信。这引出了一个问题，什么是Socket？

## 什么是套接字

套接字是网络上运行的两个程序之间的双向通信链路的一个端点。端点是IP地址和端口号的组合。套接字绑定到端口号，以便TCP层可以标识要发送到的数据的应用程序。

当程序在网络上运行时，可以从本地位置以外的其他位置进行访问。在不同的位置，我的意思是同一网络上的所有计算机都可以访问它。但是，他们将如何？因此，每个程序都使用端口号注册自己。将港口号码视为大型公寓中的公寓号码。如果寄信给公寓，公寓号码会告诉邮局他应去的具体公寓。

但是，它将如何到达公寓？每个公寓都有自己独特的地址，邮局查看那些唯一的地址（实际上是一个字符串）并决定信件的目的地。在这种情况下，连接到网络的每台计算机都将拥有一个IP地址，就像通过邮局发送信件时使用的地址。同样，连接到网络的计算机需要知道同一网络上其他计算机的IP地址才能与它们通信。要与特定计算机上的特定程序通信，需要该程序的端口号。 （想想我们公寓里的公寓号码。）

## 套接字编程基础知识

套接字编程是一种连接网络上的两个节点以相互通信的方式。一个套接字（节点）侦听IP上的特定端口，而另一个套接字伸出另一个套接字以形成连接。当客户端到达服务器时，服务器形成侦听器套接字。