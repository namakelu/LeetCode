```py

class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid:
            return 0

        rows = len(grid)
        cols = len(grid[0])
        count = 0

        for row in range(rows):
            for col in range(cols):
                if grid[row][col] == '1':
                    count += 1
                    grid[row][col] = '0'
                    queue = [(row,col)]

                    while queue:
                        x,y = queue.pop()
                        for move_x, move_y in [(0,1),(0,-1),(1,0),(-1,0)]:
                            next_x = x + move_x
                            next_y = y + move_y
                            if rows > next_x >= 0 and cols > next_y >= 0 and grid[next_x][next_y] == '1':
                                grid[next_x][next_y] = '0'
                                queue.append((next_x,next_y))
                                
        return count

```
これは頭ではやりたいことが明確にあるけれども、コードの形での実装が難しいパターンだった。
特に　if rows > next_x >= 0 and cols > next_y >= 0 and grid[next_x][next_y] == '1':
ここのガード条件で大いに引っかかることが多かった。二重配列にもなれていきたい。
関数を設定して再帰的な呼び出しも考えたが、１０００回ほどで止まるという情報を見て、
汎用性のあるqueue1を使ったやり方を選択した。