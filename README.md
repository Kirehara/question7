"# question7" 
from pathlib import WindowsPath
masu=[[" ","1","2","3"],["1","?","?","?",],["2","?","?","?"],["3","?","?","?"]]
for i in range(0,4):
  print(masu[i])#マスを表示

win=0#勝ちか判定
point=0#2でそろった判定

kioku=[[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]#ループしないように行ったとこ記憶、行ったことあるなら１
def reset():#kiokuとpointリセット
  global kioku
  global point
  kioku=[[0,0,0,0],[0,0,0,0,],[0,0,0,0],[0,0,0,0]]
  point=0


def okuo(x,y):#oを置く処理
  global win
  global win
  global kioku
  try:#1～3か判定&数字かどうか
    if x<1 or x>3:
      newretu=int(input("「1～3」で置きたい列を入力"))
      x=newretu
  except  ValueError:
    print("1～3!!!!!!!")
    newretu=int(input("「1～3」で置きたい列を入力"))
    x=newretu
  try:#1～3か判定&数字かどうか
    if y<1 or y>3:
      newgyou=int(input("「1～3」で置きたい行を入力"))
      y=newgyou
  except  ValueError:
    print("1～3!!!!!!!")
    newgyou=int(input("「1～3」で置きたい行を入力"))
    y=newgyou
  if masu[x][y]=="o" or masu[x][y]=="x":#すでにおかれてるマスに置こうとしたとき
    print("すでに置かれています")
    try:#数字かどうか
      newretu=int(input("1～3で置きたい列を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      newretu=int(input("1～3で置きたい列を入力"))
    x=newretu
    try:#数字かどうか
      newgyou=int(input("1～3で置きたい行を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      newgyou=int(input("1～3で置きたい行を入力"))
    y=newgyou
    try:#1～3か判定&数字かどうか
      if x<1 or x>3:
        newretu=int(input("「1～3」で置きたい列を入力"))
        x=newretu
    except  ValueError:
      print("1～3!!!!!!!")
      newretu=int(input("「1～3」で置きたい列を入力"))
      x=newretu
    try:#1～3か判定&数字かどうか
      if y<1 or y>3:
        newgyou=int(input("「1～3」で置きたい行を入力"))
        y=newgyou
    except  ValueError:
      print("1～3!!!!!!!")
      newgyou=int(input("「1～3」で置きたい行を入力"))
      y=newgyou
  masu[x][y]="o"#oを置く
  naname(x,y)
  reset()
  naname2(x,y)
  reset()
  tate(x,y)
  reset()
  yoko(x,y)
  reset()
  for i in range(0,4):
    print(masu[i])#マスを表示

def okux(x,y):#oのときと同じ仕組みでx置く処理
  global win
  global kioku
  global point
  try:
    if x<1 or x>3:
      newretu=int(input("「1～3」で置きたい列を入力"))
      x=newretu
  except  ValueError:
    print("1～3!!!!!!!")
    newretu=int(input("「1～3」で置きたい列を入力"))
    x=newretu
  try:
    if y<1 or y>3:
      newgyou=int(input("「1～3」で置きたい行を入力"))
      y=newgyou
  except  ValueError:
    print("1～3!!!!!!!")
    newgyou=int(input("「1～3」で置きたい行を入力"))
    y=newgyou
  if masu[x][y]=="o" or masu[x][y]=="x":
    print("すでに置かれています")
    try:
      newretu=int(input("1～3で置きたい列を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      newretu=int(input("1～3で置きたい列を入力"))
    x=newretu
    try:
      newgyou=int(input("1～3で置きたい行を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      newgyou=int(input("1～3で置きたい行を入力"))
    y=newgyou
    try:
      if x<1 or x>3:
        newretu=int(input("「1～3」で置きたい列を入力"))
        x=newretu
    except  ValueError:
      print("1～3!!!!!!!")
      newretu=int(input("「1～3」で置きたい列を入力"))
      x=newretu
    try:
      if y<1 or y>3:
        newgyou=int(input("「1～3」で置きたい行を入力"))
        y=newgyou
    except  ValueError:
      print("1～3!!!!!!!")
      newgyou=int(input("「1～3」で置きたい行を入力"))
      y=newgyou
  masu[x][y]="x"#xを置く
  naname(x,y)
  reset()
  naname2(x,y)
  reset()
  tate(x,y)
  reset()
  yoko(x,y)
  reset()
  if win==10:#xのときwinが10なら20に変えることによってxが勝つ処理行う
    win=20
  for i in range(0,4):
    print(masu[i])#マスを表示


def naname(x,y):#左斜め判定
  global point
  global win
  global kioku
  kioku[x][y]=1#行ったことあることにする
  if x-1>0 and y-1>0:#左斜め上が範囲内なら
    if kioku[x-1][y-1]==0:#左斜め上が行ったことないなら
      if masu[x][y]==masu[x-1][y-1]:#左斜め上と同じなら
        point+=1
        naname(x-1,y-1)
  if x+1<4 and y+1<4:#右下が範囲内なら
    if kioku[x+1][y+1]==0:#右下が行ったことないなら
      if masu[x][y]==masu[x+1][y+1]:#右下と同じなら
        point+=1
        naname(x+1,y+1)
  if point>=2:#point２以上なら勝ちにしたい
    win=10


def naname2(x,y):#右ななめ判定
  global point
  global win
  global kioku
  kioku[x][y]=1#行ったことあることにする
  if x-1>0 and y+1<4:#左下が範囲内なら
    if kioku[x-1][y+1]==0:#左下が行ったことないなら
      if masu[x][y]==masu[x-1][y+1]:#左下と同じなら
        point+=1
        naname2(x-1,y+1)
  if x+1<4 and y-1>0:#右上が範囲内なら
    if kioku[x+1][y-1]==0:#右上が行ったことないなら
      if masu[x][y]==masu[x+1][y-1]:#右上と同じなら
        point+=1
        naname2(x+1,y-1)
  if point>=2:#point２以上なら勝ちにしたい
    win=10

def yoko(x,y):#横判定
  global point
  global win
  global kioku
  kioku[x][y]=1#行ったことあることにする
  if y-1>0:#上が範囲内なら
    if kioku[x][y-1]==0:#上が行ったことないなら
      if masu[x][y]==masu[x][y-1]:#上と同じなら
        point+=1
        yoko(x,y-1)
  if y+1<4:#下が範囲内なら
    if kioku[x][y+1]==0:#下が行ったことないなら
      if masu[x][y]==masu[x][y+1]:#下と同じなら
        point+=1
        yoko(x,y+1)
  if point>=2:#point２以上なら勝ちにしたい
    win=10

def tate(x,y):#縦判定
  global point
  global win
  global kioku
  kioku[x][y]=1#行ったことあることにする
  if x-1>0:#左が範囲内なら
    if kioku[x-1][y]==0:#左が行ったことないなら
      if masu[x][y]==masu[x-1][y]:#左と同じなら
        point+=1
        tate(x-1,y)
  if x+1<4:#右が範囲内なら
    if kioku[x+1][y]==0:#右が行ったことないなら
      if masu[x][y]==masu[x+1][y]:#右と同じなら
        point+=1
        tate(x+1,y)
  if point>=2:#point２以上なら勝ちにしたい
    win=10

while win<5:#最大五回ループ
  point=0
  win+=1
  print("oの番")
  try:#数字かどうか
    retu=int(input("1～3で置きたい列を入力"))
  except  ValueError:
    print("1～3!!!!!!!")
    retu=int(input("1～3で置きたい列を入力"))
  try:#数字かどうか
    gyou=int(input("1～3で置きたい行を入力"))
  except  ValueError:
    print("1～3!!!!!!!")
    gyou=int(input("1～3で置きたい行を入力"))
  okuo(retu,gyou)
  if win<5:#これで5回目のoで終わる
    print("xの番")
    try:#数字かどうか
      retu=int(input("1～3で置きたい列を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      retu=int(input("1～3で置きたい列を入力"))
    try:#数字かどうか
      gyou=int(input("1～3で置きたい行を入力"))
    except  ValueError:
      print("1～3!!!!!!!")
      gyou=int(input("1～3で置きたい行を入力"))
    okux(retu,gyou)

if win==10:
  print("oの勝ち")
elif win==20:
  print("xの勝ち")
else:
  print("引き分け")




