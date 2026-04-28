---
title: ACM输入输出格式
published: 2026-04-28
pinned: true
description:
tags:
category: Java
author: WangKaiCode
sourceLink: https://github.com/WangKaiCode/TechBlog/src/content/posts/
draft: true
date: 2026-04-28
image: '""'
---
# ACM输入输出格式
## 已知输入数据结构
```java
import java.io.*;

class Main{
    
    public static void main(string[] args){
        //创建输入缓冲流BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        //
        StreamTokenizer in = new StreamTokenizer(br);
        //创建输出缓冲流PrintWriter
        PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
        while (in.nextToken() != StreamTokenizer.TT_EOF){
            int A = (int) in.nval;
            in.nextToken();
            int B = (int) in.nval;
            out.println(A+B);
        }
        out.flush();
        out.close();
    }
}
```
## 输入数据结构变化未知
```java
import java.io.*;
class Main{
	public static void main(String[] args) throws IOException {
        
	    //创建输入缓冲流BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        //创建输出缓冲流PrintWriter
        PrintWriter out = new PrintWriter(new OutputStreamWriter(System.out));
        String line;
        
        while ((line = br.readLine())!=null){//readLine将一行数据包括空格传给string 
            String[] parts = line.split(" ");//字符串分割后得到字符串数组
            int sum = 0;
            for (String num : parts) {
                sum += Integer.valueOf(num);//将字符串数组进行类型转换装箱使用
            }
            out.println(sum);
        }
        out.flush();
        out.close();



    }
}
```
## 考虑全局静态变量





