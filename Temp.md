1.
  学生（Student）  ：S(Sno, Sname, Sbirth, Dept, Class, Dorm)
   极小函数依赖集：Sno → Sname, Sno → Sbirth, Sno → Class, Class → Dept, Dept → Dorm
  班级（Class）  ：C(Class, Major, Dept, Cnum, Cyear)
   极小函数依赖集：Class → Major, Class → Dept, Class → Cnum, Class → Cyear
  系（Department）  ：D(Dept, Dno, Dloc, Dnum)
   极小函数依赖集：Dept → Dno, Dno → Dept, Dno → Dloc, Dno → Dnum
  学会（Society）  ：So(Sname, Fyear, Sloc, Snum)
   极小函数依赖集：Sname → Fyear, Sname → Sloc, Sname → Snum
  学生    学会（Student    Society）  ：SS(Sno, Sname, JoinYear)
   极小函数依赖集：(Sno, Sname) → JoinYear
2.
  学生关系（S）  ：Sno → Class → Dept → Dorm
3.
  学生    学会关系（SS）  中(Sno, Sname) → JoinYear ：这是  完全函数依赖  
4.
     学生关系（S）  ：
       候选码：Sno
       外部码：Class、Dept
       无全码 
     班级关系（C）  ：
       候选码：Class、(Major, Cyear) 
       外部码：Dept
       无全码 
     系关系（D）  ：
       候选码：Dept、Dno
       无外部码
       无全码 
     学会关系（So）  ：
       候选码：Sname
       无外部码 
       无全码 
     学生    学会关系（SS）  ：
       候选码：(Sno, Sname) 
       外部码：Sno、Sname
       无全码 