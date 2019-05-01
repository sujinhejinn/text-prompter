# -*- coding: utf-8 -*-
"""
import os
import os.path
rootdir = "e:/data_crawler"                                   # 指明被遍历的文件夹

for parent,dirnames,filenames in os.walk(rootdir):    #三个参数：分别返回1.父目录 2.所有文件夹名字（不含路径） 3.所有文件名字
    for dirname in  dirnames:                       #输出文件夹信息
        print( "parent is:" + parent)
        print(  "dirname is" + dirname)
    
    for filename in filenames:                        #输出文件信息
        print( "parent is:" + parent)
        print( "filename is:" + filename)
        print( "the full name of the file is:" + os.path.join(parent,filename)) #输出文件路径信息
"""        
import speech_recognition as sr
import re
import tkinter as tk
from tkinter import filedialog
#import pyttsx3
import string
 
def removePunctuation(text):
    '''去掉字符串中标点符号
    '''
    #方法一：使用列表添加每个字符，最后将列表拼接成字符串，目测要五行代码以上
    temp = []
    for c in text:
        if c not in string.punctuation:
            temp.append(c)
    newText = ''.join(temp)
    #方法二：给join传递入参时计算符合条件的字符
    #b = ''.join(c for c in text if c not in string.punctuation)
    #print(b)

    return newText

root = tk.Tk()
root.withdraw()
file_path = filedialog.askopenfilename()

#engine = pyttsx3.init()

file = open(file_path,'r+', encoding='UTF-8')# 打开文件
poem = []
#i = 0
for line in file: # 遍历file文件
    #print(removePunctuation(line)) # 循环打印文件中每一行内容
    #poem.append(removePunctuation(line))
    print( re.sub("[\s+\.\!\/_,$%^*(+\"\']+|[+——！，。？、~@#￥%……&*（）]+".encode('utf-8').decode('utf-8'), "".encode('utf-8').decode('utf-8'),line))
    poem.append( re.sub("[\s+\.\!\/_,$%^*(+\"\']+|[+——！，。？、~@#￥%……&*（）]+".encode('utf-8').decode('utf-8'), "".encode('utf-8').decode('utf-8'),line))              
#    i += 1
#    engine.say(line)
#    engine.runAndWait()
    #print(type(line)) # <class 'str'> 类型是字符串
file.close()# 关闭文件

stop_sign = True
i_poem = 0
while stop_sign:
    r = sr.Recognizer()
    mic = sr.Microphone()

    print(poem[i_poem])
    print('录音ing...')
    with mic as source:
        r.adjust_for_ambient_noise(source)
        audio = r.listen(source)
    print('录音结束，识别ing...')
    trying = r.recognize_google(audio, language='cmn-Hans-CN', show_all=True)

    print('分析语音')
    if trying:
        for t in trying['alternative']:
            print(t)
            if re.search("停止", t['transcript']):
                stop_sign = False
                break
            if re.search(t['transcript'], poem[i_poem]): 
                i_poem += 1
                if i_poem == len(poem):
                    stop_sign = False
                    break


"""
fileList = fileHandle.readlines() 
for fileLine in fileList: 
    print ( fileLine )
fileHandle.close()  

import easygui
path = easygui.fileopenbox()

import tkinter as tk
from tkinter import filedialog
 
root = tk.Tk()
root.withdraw()
 
file_path = filedialog.askopenfilenames()
for f in file_path:
    fo = f.split('.')[0]+'.csv'
    with open(fo,'w') as foo:
        with open(f,'r') as fn:
            fn.readline()
            for line in fn.readlines():
                li = line.strip().split()
                foo.write('%f,%f\n'%(float(li[1]),float(li[0])))
                print(li)

       
"""
