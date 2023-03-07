Не получилось воспроизвести ошибку одновременного обращения к элементу массива counters со стороны нескольких параллельно запущенных потоков

Суть в этом куске кода:
```
void CountingSortParallel(int[] inputArray, int[] counters, int offset, int startPos, int endPos)
{
    for (int i = startPos; i < endPos; i++)
    {
        //lock (lock_object)
        {
            counters[inputArray[i] + offset]++;
        }
    }
}
```
С закомментированной строкой //lock (lock_object) должны получать непредсказуемый результат, но чаще False, чем True (Это результат функции EqualityMatrix).
Однако всегда получаем True, что озадачивает. Не запускается несколько параллельных процессов?     