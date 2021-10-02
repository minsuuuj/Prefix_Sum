# Prefix_Sum

최초로 생각한 알고리즘 :

      from array import *

      n,h = map(int,input('').split(' '))

      cave = array('i',[0]*h)    # 0으로 초기화된 h길이의 배열 생성
      # index 0 에 높이 h의 data 저장

      for i in range(n):
          k = int(input(''))  # 종유석 or 석순 길이 입력
          if i % 2 == 0 : # 석순일때
              for j in range(k) :
                  cave[h-1-j] += 1  
      # 석순인 경우, 높이 1에서부터 높이 k까지 벽을 추가한다.
      
          else :  # 종유석일 때
              for j in range(k) :
                  cave[j] += 1
      # 종유석인 경우, 높이 h에서부터 높이 h-k까지 벽을 추가한다.

      print(min(cave),cave.count(min(cave)))
 
이 답은 시간초과로 오답처리가 되었다.

이중 for문의 시간복잡도가 문제라고 생각하여 2중 for문을 없애는 방향으로 생각해보았다.

초기에 이중 for문을 쓴 까닭은 석순or종유석의 길이를 입력받은 후 바로 처리하고 위해서였다.
그래서 입력을 받아 효율적으로 저장한 후, 처리하는 방향으로 고민해보았다.

각 높이가 입력된 횟수를 저장하면 각 높이에 있는 장애물의 갯수를 계산할 수 있다.
(석순의 경우, 더 큰 높이의 값이 존재한다면 그 이하의 높이에서도 당연히 존재하기 때문, 종유석의 경우 반대)
이를 위해 석순과 종유석의 정보를 따로 입력받는 것이 필수적이었다.

      from array import *

      n,h = map(int,input('').split(' '))

      down = array('i',[0]*h)    # 석순
      up = array('i',[0]*h)    # 종유석

      for i in range(n):  # 석순과 종유석 길이 data를 따로 저장
          if i % 2 == :
              down[int(input(''))-1] += 1
          else :
              up[int(input(''))-1] += 1
      # 각 높이에 해당하는 인덱스의 value를 1씩 증가시키며 저장
      
      for i in range(h - 1, 0, -1):
          down[i] += down[i + 1]
          up[i] += up[i + 1]
