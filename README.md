# Код
import java.util.ArrayList;
import java.util.List;

public class SILab2 {

    public static List<String> function(List<String> list) { // во графот почнувам од овој ред на кодот кој што ми е означен со број 6 а надолу одат редоследно 7,8,9..
        if (list.size() <= 0) {
            throw new IllegalArgumentException("List length should be greater than 0");
        }
        int n = list.size();
        int rootOfN = (int) Math.sqrt(n);
        if (rootOfN * rootOfN  != n) {
            throw new IllegalArgumentException("List length should be a perfect square");
        }
        List<String> numMines = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            if (!list.get(i).equals("#")) {
                int num = 0;
                if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) || (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ) {
                    if ( (i % rootOfN != 0 && list.get(i - 1).equals("#")) && (i % rootOfN != rootOfN - 1 && list.get(i + 1).equals("#")) ){
                        num += 2;
                    }
                    else {
                        num  += 1;
                    }
                }
                if (i - rootOfN >= 0 && list.get(i - rootOfN).equals("#")){
                    num++;
                }
                if (i + rootOfN < n && list.get(i + rootOfN).equals("#")){
                    num++;
                }
                numMines.add(String.valueOf(num));
            }
            else {
                numMines.add(list.get(i));
            }
        }
        return numMines;
    }
}
# Стефани Бошкова 203004
# Control Flow Graph
  ![cfg1](https://user-images.githubusercontent.com/101138892/171933351-a379eb66-1022-413d-ac14-a31efc3e2312.png)

# Цикломатска комплексност
  Цикломатската комплексност ја добиваме со формулата Р+1. Во овој случај бројот на предикатни јазли, Р=8 што значи дека цикломатската комплексност е 9.
# Тест случаи според критериумот Every statement
  -Тест случај 1 : празна низа -> ги опфаќа 7,8
  -Тест случај 2 : низа од 3 броја -> ги опфаќа 10,11,12,13
  -Тест случај 3 : низа од 9 броја -> ги опфаќа 10,11,15,16,17,18,19,20,21,23,24,27,28,30,31,33,35,36,39
# Тест случаи според критериумот Every branch
  -Тест случај 1 : празна низа -> ги опфаќа 7->8->end
  -Тест случај 2 : низа од 3 броја -> ги опфаќа 10->11->12->13->end
  -Тест случај 3 : низа од 9 броја -> ги опфаќа сите останати

  
  
