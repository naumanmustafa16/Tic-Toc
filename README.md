# Tic-Toc
# write your code here


a = '         '
a_list = []
player = 'xx'
counter = 0
end = 0
draw = 0
while True:
      def nest_list1(a):
            global a_list
            x = 0
            for i in range(3):
                  a_list.append([])
                  for j in range(3):
                        a_list[i].append(a[x])
                        x = x + 1
            return a_list


      def display():
             print(f'---------\n'
                   f'| {a_list[0][0]} {a_list[0][1]} {a_list[0][2]} |\n'
                  f'| {a_list[1][0]} {a_list[1][1]} {a_list[1][2]} |\n'
                  f'| {a_list[2][0]} {a_list[2][1]} {a_list[2][2]} |\n'
                  f'---------')

      def nest_list2(c1,c2):
            global a_list
            global player
            global counter
            c1 = int(c1)
            c2 = int(c2)
            if player == 'xx':
                  if a_list[c1-1][c2-1] == ' ':
                        a_list[c1-1][c2-1] = 'X'
                        counter = counter + 1
                        # print(counter)
                        display()
                        player = 'oo'
                        if counter >= 5:
                              win_check()
                              win_display(win_list)
                        else:
                              take_input()

                  else:
                        print('This cell is occupied! Choose another one!')
                        take_input()
            elif player == 'oo':
                  if a_list[c1-1][c2-1] == ' ':
                        a_list[c1-1][c2-1] = 'O'
                        counter = counter + 1
                        # print(counter)
                        display()
                        player = 'xx'
                        if counter >= 5:
                              win_check()
                              win_display(win_list)
                              # print(counter)
                        else:
                              take_input()
                  else:
                        print('This cell is occupied! Choose another one!')
                        take_input()


      def take_input():
            while True:
                  try:
                        c1,c2 = input().split()
                  except ValueError:
                        print('You should enter numbers!')
                        continue

                  try:
                        nest_list2(c1,c2)
                  except IndexError:
                        print('Coordinates should be from 1 to 3!')
                  except ValueError:
                        print('You should enter numbers!')
                  except NameError:
                        pass
                  else:
                        break



      win_list =[]
      def win_check():
# Diagonal Check
            global win_list
            if ((a_list[0][0] == a_list[1][1] == a_list[2][2]) or (a_list[2][0] == a_list[1][1] == a_list[0][2])) and a_list[1][1] == 'X':
                  win_list.append(1)
                  return win_list
            if ((a_list[0][0] == a_list[1][1] == a_list[2][2]) or (a_list[2][0] == a_list[1][1] == a_list[0][2])) and a_list[1][1] == 'O':
                  win_list.append(2)
# coloumns Check
# 1st Coloumn
            if (a_list[0][0] == a_list[1][0] == a_list[2][0]) and a_list[0][0] == 'X':
                  win_list.append(3)

            if (a_list[0][0] == a_list[1][0] == a_list[2][0]) and a_list[0][0] == 'O':
                  win_list.append(4)

# 2nd Coloumn
            if (a_list[0][1] == a_list[1][1] == a_list[2][1]) and a_list[0][1] == 'X':
                  win_list.append(5)

            if (a_list[0][1] == a_list[1][1] == a_list[2][1]) and a_list[0][1] == 'O':
                  win_list.append(6)
                  # return win_list
      # 3rd Coloumn
            if (a_list[0][2] == a_list[1][2] == a_list[2][2]) and a_list[0][2] == 'X':
                  win_list.append(7)
                  # return win_list
            if (a_list[0][2] == a_list[1][2] == a_list[2][2]) and a_list[0][2] == 'O':
                  win_list.append(8)
                  # return win_list
      # Rows Check
      # 1st Row
            if (a_list[0][0] == a_list[0][1] == a_list[0][2]) and a_list[0][0] == 'X':
                  win_list.append(9)
            if (a_list[0][0] == a_list[0][1] == a_list[0][2]) and a_list[0][0] == 'O':
                  win_list.append(10)
      # 2nd Row
            if (a_list[1][0] == a_list[1][1] == a_list[1][2]) and a_list[1][0] == 'X':
                  win_list.append(11)
            if (a_list[1][0] == a_list[1][1] == a_list[1][2]) and a_list[1][0] == 'O':
                  win_list.append(12)
      # 3rd Row
            if (a_list[2][0] == a_list[2][1] == a_list[2][2]) and a_list[2][0] == 'X':
                  win_list.append(13)
            if (a_list[2][0] == a_list[2][1] == a_list[2][2]) and a_list[2][0] == 'O':
                  win_list.append(14)
            return win_list


      draw_list = []


      def draw_check():
            global a
            global draw
            # if len(win_list) == 0:
            print('Draw')
            draw = 1


      if draw == 1:
            break


      def win_display(win_list):
            global end
            if len(win_list) == 1:
                  if win_list[0] % 2 == 0:
                        print('O wins')
                        end = 1
                  else:
                        print('X wins')
                        end = 1
            else:
                  if counter == 9:
                        draw_check()
                  else:
                        take_input()
      if end == 1:
            break

            not_finished_list = []
      def game_not_finished():
            global a
            if ((('_' in a) or (' ' in a)) and (len(impossible_list) == 0) and len(win_list) == 0):
                  print('Game not finished')
                  not_finished_list.append(1)
            return not_finished_list
      impossible_list = []
      def impossible():
            global a
            X = a.count('X')
            O = a.count('O')

            if  len(win_list) > 1 or (X - O < -1 or X - O > 1):
                  print('Impossible')
                  impossible_list.append(1)
            return impossible_list

      nest_list1(a)
      display()
      take_input()

