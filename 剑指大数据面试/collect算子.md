   * This method should only be used if the resulting array is expected to be small, as all the data is loaded into the driver's memory.
   * 这个方法会把RDD中所有的数据都加载到driver内存当中，可能会导致OOM，慎用。
   * 如果一定要用，可以使用take(),取出前面几条。或者使用saveAsTextFile

