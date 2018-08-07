#Arrays.sort() with comparator

class Solution {
    
    public static class MyComparator implements Comparator<Interval> {
        public int compare(Interval a, Interval b) {
            if (a.start < b.start)
                return -1;
            else if(a.start == b.start)
                return 0;
            else
                return 1;
        }
    };
    public boolean canAttendMeetings(Interval[] intervals) {
          Arrays.sort(intervals, new MyComparator());
          boolean result = true;
          for(int i = 0; i < intervals.length - 1; i++) {
              if(intervals[i].end > intervals[i+1].start)
                  result = false;
          }
        return result;
    }
}
