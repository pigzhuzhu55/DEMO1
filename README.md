**DEMO1**

取多个时间段的重叠算法

  
```
public class TimeTime
    {

        public DateTime BeginTime { get; set; }

        public DateTime EndTime { get; set; }

    }

private List<Betime> timeList = new List<Betime>() { 

    new TimeTime{BeginTime=new DateTime(2018,3,1,10,55,0),EndTime=new DateTime(2018,3,1,11,34,0)},

    new TimeTime{BeginTime=new DateTime(2018,3,1,13,9,34),EndTime=new DateTime(2018,3,1,17,45,23)},

    new TimeTime{BeginTime=new DateTime(2018,3,1,14,23,12),EndTime=new DateTime(2018,3,1,15,24,14)},

    new TimeTime{BeginTime=new DateTime(2018,3,1,7,38,56),EndTime=new DateTime(2018,3,1,10,34,45)},

    new TimeTime{BeginTime=new DateTime(2018,3,1,6,10,58),EndTime=new DateTime(2018,3,1,8,15,28)},

    new TimeTime{BeginTime=new DateTime(2018,3,1,16,14,25),EndTime=new DateTime(2018,3,1,17,52,15)}

};

for (int i = 0; i < timeList.Count()- 1; i++)
{

    int j = i + 1;

    var ti = timeList.ElementAt(i);

    var tj = timeList.ElementAt(j);

    //前面一条数据的结束时间比后天一条数据的开始时间大
    if (ti.EndTime >= tj.BeginTime)
    {
        tj.BeginTime = ti.BeginTime;
        //前面一条数据的结束时间比后面一条数据结束时间大的情况
        if (ti.EndTime >= tj.EndTime)
        {
            tj.EndTime = ti.EndTime;
        }
        timeList.RemoveAt(i);
        i--;
    }

}

  foreach (var time1 in timeList)
  { 

      Console.WriteLine($"{time1.BeginTime.ToString("HH:mm")}-{time1.EndTime.ToString("HH:mm")}"); 

  }
```
