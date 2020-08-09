# 十种常用算法

## 二分查找算法（非递归）

```

public class BinarySearchNoRecursion {

    public static void main(String[] args) {
        // 测试
        int[] arr = {1, 3, 8, 10, 11, 67, 100};
        int index = binarySearch(arr, 4);
        System.out.println("index：" + index);
    }

    // 二分查找的非递归实现

    /**
     * @param arr    待查找的数组，arr是升序排序
     * @param target 需要查找的数
     * @return 返回对应下标，-1表示没有找到
     */
    public static int binarySearch(int[] arr, int target) {

        int left = 0;
        int right = arr.length - 1;
        while (left <= right) { // 判断继续查找条件
            int mid = (left + right) / 2;
            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] > target) {
                right = mid - 1; // 需要向左边查找
            } else {
                left = mid + 1; // 需要向右边查找
            }
        }
        return -1;
    }
}

```

## 分治算法

```

public class DivideAndConquer {

    public static void main(String[] args) {
        hanoiTower(10, 'A', 'B', 'C');
    }

    // 汉诺塔的移动方法
    // 使用分治算法
    public static void hanoiTower(int num, char a, char b, char c) {
        // 如果只有一个盘
        if (num == 1) {
            System.out.println("第1个盘从 " + a + " -> " + c);
        } else {
            // 如果我们有 n >= 2 的情况，我们总是看做是两个盘，最下边的盘和上面的盘
            // 1.先把最上边的盘 A -> B，移动过程会使用到c
            hanoiTower(num - 1, a, c, b);
            // 2.把最下边的盘 A -> C
            System.out.println("第" + num + "个盘从 " + a + " -> " + c);
            // 3.把B塔的所有盘移动到C，移动过程使用到a塔
            hanoiTower(num - 1, b, a, c);
        }
    }
}

```

