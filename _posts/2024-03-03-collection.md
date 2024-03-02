---
layout: single
title: "Java Collection"
categories:
  - 자바 이론
toc: true
author_profiles: false
sidebar:
  nav: "docs"
tags:
  - Java
---


# collection

- **컬렉션(Collection)이란?**
여러 개의 다양한 데이터들을 쉽고 효과적으로 처리할 수 있도록 표준화 된 방법을 제공하는 클래스들의 집합
(데이터를 효율적으로 저장하는 자료구조와 데이터를 처리하는 알고리즘이 미리 구현되어 있음)

# 컬렉션의 주요 인터페이스

- **Iterator**
    
    컬렉션에 저장된 요소를 접근하는데 사용되는 인터페이스
    List와 Set계열에서만 사용
    (Map의 경우 Set 또는 List화 시켜서 iterator()를 사용)
    
- Collection 계열
    - list 계열 - 자료들을 순차적으로 나열한 자료구조로 인덱스로 관리되며, 중복해서 인스턴스 저장이 가능
        - **AllayList**
            
            ```java
            List<String> stringList = new ArrayList<>();
                    stringList.add("안");
                    stringList.add("녕");
                    stringList.add("하");
                    stringList.add("세");
                    stringList.add("요");
            ```
            
        - **LinkedList**
            
            이중연결리스트
            
            ```java
            List<String> linkedList = new LinkedList<>();
                    linkedList.add("apple");
                    linkedList.add("banana");
                    linkedList.add("orange");
                    linkedList.add("mango");
                    linkedList.add("grape");
            ```
            
    - **set 계열**
        
        저장 순서가 유지되지 않고, 중복 인스턴스도 저장하지 못하게 하는 자료구조
        (null값도 중복하지 않게 하나의 null만 저장)
        
        구현 클래스 : HashSet, LinkedHashSet, TreeSet
        
        - **Hashset**
            
            ```java
            HashSet<String> hset = new HashSet<>();
            
                    hset.add("java");
                    hset.add("mysql");
                    hset.add("jdbc");
                    hset.add("html");
                    hset.add("css");
            ```
            
            *`/* 목차. 1. toArray() : 배열로 바꿈`* 
            
            `Object[] arr = hset.toArray();`
            
        - **LinkedHashSet**
        HashSet과 거의 동일하지만 Set에 추가되는 순서를 유지함
        - **Treeset**
            
            이진 트리를 기반으로 한 Set컬렉션으로, 왼쪽과 오른쪽 자식 노드를 참조하기 위한 두 개의 변수로 구성
            
- Map 계열
    - 키(key)와 값(value)으로 구성되어 있으며, 키와 값은 모두 인스턴스
    - 키는 중복 저장을 허용하지 않고(Set방식), 값은 중복 저장 가능(List방식)
    - 키가 중복되는 경우, 기존에 있는 키에 해당하는 값을 덮어 씀
    - 구현 클래스 : HashMap, HashTable, LinkedHashMap, Properties, TreeMap
    
     **HashMap**
    
    ```java
    HashMap hmap = new HashMap();
            
            hmap.put("one", new Date()); 
            hmap.put(12,"red apple");
            hmap.put(33,123);
    ```
    
    **Properties**
    
    HashMap 을 구혀야여 사용 용법이 거의 유사하지만 Key와 value 모두 문자열만 사용할 수 있는 자료구조 이다.
    
    ```java
    Properties prop = new Properties();
            
            prop.setProperty("driver", "com.mysql.cj.jdbc.Driver");
            prop.setProperty("url", "jdbc:mysql://localhost/menu");
            prop.setProperty("user", "ohgiraffers");
            prop.setProperty("password", "ohgiraffers");
    ```
    
- **Stack  (메소드 구조)**
    
    stack은 제한적으로 접근할 수 있는 나열 구조로 데이터를 저장
    **후입선출**(LIFO - Last Input First Out)방식의 자료 구조
    
    ```java
    Stack<Integer> integerStack = new Stack<>();
            //필기. 값을 넣을 때는 push()메소드를 이용한다. add() 도 가능하다
    
            integerStack.push(1);
            integerStack.push(2);
    ```
    
    *`peek() : 해당 스택의 가장 마지막에 있는(상단) 요소 반환`*
    
    *`pop() : 해당 스택의 가장 마지막에 있는 (상단) 요소 반환 후 제거`*
    
- **Queue (터널구조)**
    
    queue는 선형 메모리 공간에 데이터를 저장
    
    **선입선출**(FIFO - First Input First Out)방식의 자료구조
    
    ```java
    Queue<String> que = new LinkedList<>();
    
            que.offer("first");
            que.offer("second");
            que.offer("third");
            que.offer("fourth");
            que.offer("fifth");
    ```
    
    *`peek() : 해당 큐에 가장 앞에 있는 요소 ( 먼저 들어온 요소) 를 반환`*
    
    *`poll() : 해당 큐에 가장 앞에 있는 요소(먼저들어온 요소) 를 반환후 제거`*
    

# 사용용도

1. **ArrayList:**
    - 사용 시나리오: 순차적으로 자료를 추가하고 읽을 때, 요소의 접근과 순회가 빈번할 때.
    - 주의 사항: 중간에 요소를 삽입하거나 삭제하는 연산은 비효율적.
2. **LinkedList:**
    - 사용 시나리오: 자주 데이터를 중간에 삽입 또는 삭제할 때. 큐 또는 스택을 구현할 때도 활용 가능.
    - 주의 사항: 요소의 삽입과 삭제는 상대적으로 빠르지만, 인덱스를 통한 접근이 느리다.
3. **Stack:**
    - 사용 시나리오: 후입선출(LIFO) 구조의 데이터 관리 시. 메서드 호출을 추적하거나, 깊이 우선 탐색 등에 사용.
    - 주의 사항: Java 6부터는 **`Deque`** 인터페이스의 **`ArrayDeque`** 클래스가 스택과 큐를 모두 지원하여 권장됨.
4. **Queue:**
    - 사용 시나리오: 선입선출(FIFO) 구조의 데이터 관리 시. 대기열이나 태스크 처리에 사용.
    - 주의 사항: Java에서는 **`LinkedList`**를 이용하여 **`Queue`** 인터페이스를 구현.
5. **HashSet:**
    - 사용 시나리오: 중복을 허용하지 않고, 순서가 중요하지 않을 때. 검색, 삽입, 삭제가 빈번하게 발생할 때 효율적.
    - 주의 사항: 순서가 중요한 경우 **`LinkedHashSet`** 또는 **`TreeSet`**을 사용.
6. **LinkedHashSet:**
    - 사용 시나리오: 순서를 유지하면서 중복을 허용하지 않을 때. 순서가 중요한 데이터 저장 시.
    - 주의 사항: 검색, 삽입, 삭제는 **`HashSet`**보다는 느리지만, **`HashSet`**보다는 빠르다.
7. **TreeSet:**
    - 사용 시나리오: 정렬된 순서로 요소를 저장하고자 할 때. 검색, 삽입, 삭제가 빈번하지 않을 때.
    - 주의 사항: 정렬된 순서를 유지하기 위해 **`Comparable`** 또는 **`Comparator`**를 구현해야 함.
8. **HashMap:**
    - 사용 시나리오: Key-Value 쌍으로 데이터를 저장할 때. 검색, 삽입, 삭제가 빈번하게 발생할 때 효율적.
    - 주의 사항: 순서가 중요한 경우 **`LinkedHashMap`**을 사용.
9. **Properties:**
    - 사용 시나리오: 설정 파일이나 속성 파일을 다룰 때. Key와 Value가 문자열인 간단한 맵을 사용할 때.
    - 주의 사항: **`HashTable`**을 상속받아 구현되어 있으며, 주로 설정 정보를 관리하는 데 활용.