# 格式化时间日期
[How do I format a date with Dart?](https://stackoverflow.com/questions/16126579/how-do-i-format-a-date-with-dart)

___



> 1

可以使用[`intl`](https://www.dartdocs.org/documentation/intl/latest/intl/DateFormat-class.html) 包来初始化

```
import 'package:intl/intl.dart';

main() {
  final DateTime now = DateTime.now();
  final DateFormat formatter = DateFormat('yyyy-MM-dd');
  final String formatted = formatter.format(now);
  print(formatted); // something like 2013-04-20
}
```

对应的格式

```
ICU Name                   Skeleton
--------                   --------
DAY                          d
ABBR_WEEKDAY                 E
WEEKDAY                      EEEE
ABBR_STANDALONE_MONTH        LLL
STANDALONE_MONTH             LLLL
NUM_MONTH                    M
NUM_MONTH_DAY                Md
NUM_MONTH_WEEKDAY_DAY        MEd
ABBR_MONTH                   MMM
ABBR_MONTH_DAY               MMMd
ABBR_MONTH_WEEKDAY_DAY       MMMEd
MONTH                        MMMM
MONTH_DAY                    MMMMd
MONTH_WEEKDAY_DAY            MMMMEEEEd
ABBR_QUARTER                 QQQ
QUARTER                      QQQQ
YEAR                         y
YEAR_NUM_MONTH               yM
YEAR_NUM_MONTH_DAY           yMd
YEAR_NUM_MONTH_WEEKDAY_DAY   yMEd
YEAR_ABBR_MONTH              yMMM
YEAR_ABBR_MONTH_DAY          yMMMd
YEAR_ABBR_MONTH_WEEKDAY_DAY  yMMMEd
YEAR_MONTH                   yMMMM
YEAR_MONTH_DAY               yMMMMd
YEAR_MONTH_WEEKDAY_DAY       yMMMMEEEEd
YEAR_ABBR_QUARTER            yQQQ
YEAR_QUARTER                 yQQQQ
HOUR24                       H
HOUR24_MINUTE                Hm
HOUR24_MINUTE_SECOND         Hms
HOUR                         j
HOUR_MINUTE                  jm
HOUR_MINUTE_SECOND           jms
HOUR_MINUTE_GENERIC_TZ       jmv
HOUR_MINUTE_TZ               jmz
HOUR_GENERIC_TZ              jv
HOUR_TZ                      jz
MINUTE                       m
MINUTE_SECOND                ms
SECOND                       s
```







