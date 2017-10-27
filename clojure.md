title: clojure 介绍

speaker: Brain

url: https://github.com/clojure/clojure

transition: slide3

files: /js/demo.js,/css/demo.css,/js/zoom.js

theme: moon

usemathjax: yes


[slide]("a")

# Lisp and Clojure

## S表达式
### 看破红尘出家数括号 

[core.clj]("https://github.com/clojure/clojure/blob/master/src/clj/clojure/core.clj")

[slide]("b")

xml json s-exp

## xml ant build.xml

[build.xml]("https://github.com/h5bp/ant-build-script/blob/master/build.xml")

## json npm yarn packages.json
[packages.json]("https://github.com/yarnpkg/yarn/blob/master/package.json")

## s-exp project.clj
[project.clj]("https://github.com/technomancy/leiningen/blob/master/project.clj")

[slide]("d")

# List
'(a b c d)

# 函数Call

## lisp
`(functionname arg0 arg1 arg2 ...)`
    统一的形式,唯一的语义
## js
`functionname ( arg0 arg1 arg2 ...)`

## xml
```
    <functionname> 
        <arg0></arg0>
        <arg1></arg1>
        <arg2></arg2>
   </functionname>
```
[slide]("e")
#　ast 
```
(func1 arg1  (func2 arg2   (func3 arg3)))

func1(arg1 ,func2 (arg2, func3 ( arg3)))

<func1> 
    <arg1></arg1> 
    <func2> 
        <arg2></arg2> 
        <func3>
            <arg3></arg3>
        <func3>
    </func2>
</func1>
```
等价形式中,LISP　最简短
