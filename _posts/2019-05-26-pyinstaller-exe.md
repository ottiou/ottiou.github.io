---
layout: post
title:  "pyinstaller使用"
date:   2019-05-26 12:33:08 +0800
categories: python
---
# pyinstaller使用
## 配置
- 系统：windows10
- python：python3.7

## pyinstaller安装
在命令行输入
``` shell
pip install pyinstaller
```
会有Successfully installed pyinstaller的提示，表示安装成功

## 示例
先建一个python文件game.py如下:
``` py
# -*- coding:utf-8 -*-
# 摇3次骰子，当总数total，3<=total<=10时为小，11<=total<=18为大
import random
import time


def enter_stake(current_money):
	""" 输入小于结余的赌资及翻倍率,未考虑输入type错误的情况 """
	stake = int(input('How much you wanna bet?(such as 1000):'))
	rate = int(input("What multiplier do you want?你想翻几倍？(such as 2):"))
	small_compare = current_money < stake * rate
	while small_compare:
		stake = int(input('You has not so much money ${}!How much you wanna bet?(such as 1000):'.format(stake * rate)))
		rate = int(input("What multiplier do you want?你想翻几倍？(such as 2):"))
		small_compare = current_money < stake * rate
	return stake, rate


def roll_dice(times=3):
	""" 摇骰子"""
	print('<<<<<<<<<< Roll The Dice! >>>>>>>>>>')
	points_list = []
	while times > 0:
		number = random.randrange(1, 7)
		points_list.append(number)
		times = times - 1
	return points_list


def roll_result(total):
	""" 判断是大是小"""
	is_big = 11 <= total <= 18
	is_small = 3 <= total <= 10
	if is_small:
		return 'Small'
	elif is_big:
		return 'Big'


def settlement(boo, points_list, current_money, stake=1000, rate=1):
	""" 结余"""
	increase = stake * rate
	if boo:
		current_money += increase
		print('The points are ' + str(points_list) + ' .You win!')
		print('You gained $' + str(increase) + '.You have $' + str(current_money) + ' now.')
	else:
		current_money -= increase
		print('The points are ' + str(points_list) + ' .You lose!')
		print('You lost $' + str(increase) + '.You have $' + str(current_money) + ' now.')
	return current_money


def sleep_second(seconds=1):
	"""休眠"""
	time.sleep(seconds)
	# 开始游戏


def start_game():
	"""开始猜大小的游戏"""
	current_money = 1000
	print('You have ${} now.'.format(current_money))
	sleep_second()
	while current_money > 0:
		print('<<<<<<<<<<<<<<<<<<<< Game Starts! >>>>>>>>>>>>>>>>>>>>')
		your_choice = input('Big or Small: ')
		choices = ['Big', 'Small']
		if your_choice in choices:
			stake, rate = enter_stake(current_money)
			points_list = roll_dice()
			total = sum(points_list)
			actual_result = roll_result(total)
			boo = your_choice == actual_result
			current_money = settlement(boo, points_list, current_money, stake, rate)
		else:
			print('Invalid input!')
	else:
		sleep_second()
		print('Game Over!')
		sleep_second(2)


if __name__ == '__main__':
	start_game()
```
然后在game.py所在文件夹下制作一个图标文件favicon.ico，再打开命令行输入：
``` shell
pyinstaller --onefile --nowindowed --icon="favicon.ico" game.py
```
如果成功的话会提示： 
``` shell
Building EXE from EXE-00.toc completed successfully.
```
生成的exe文件在dist文件夹下面。

## 参数说明
- onefile 将结果打包成一个可执行文件
- onedir 将所有结果打包到一个文件夹中，该文件夹包括一个可执行文件和可执行文件执行时需要的依赖文件（默认）
- paths=DIR 设置导入路径
- distpath=DIR 设置将打包的结果文件放置的路径
- specpath=DIR 设置将spec文件放置的路径
- windowed 使用windows子系统执行，不会打开命令行（只对windows有效）
- nowindowed 使用控制台子系统执行（默认）（只对windows有效）
- icon="favicon.ico" 生成exe文件的图标