function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
var studentData = [{"sub1": 20, "sub2": 13, "sub3": 5}];
for (var i = 1; i < 50; i++){
  var subArr = {"sub1": getRandomIntInclusive(1, 20),
                "sub2": getRandomIntInclusive(1, 20),
                "sub3": getRandomIntInclusive(1, 20)};
  studentData.push(subArr);
}
var sortedStudentDataSub1 = {"0-4": 0, "5-8": 0, "9-12": 0, "13-16": 0, "17-20": 0};
var sortedSub1 = [0, 0, 0, 0, 0];
var sortedStudentDataSub2 = {"0-4": 0, "5-8": 0, "9-12": 0, "13-16": 0, "17-20": 0};
var sortedSub2 = [0, 0, 0, 0, 0];
var sortedStudentDataSub3 = {"0-4": 0, "5-8": 0, "9-12": 0, "13-16": 0, "17-20": 0};
var sortedSub3 = [0, 0, 0, 0, 0];
for (var i = 0; i < 50; i++){
  if (studentData[i].sub1 < 5){
    sortedStudentDataSub1["0-4"]++;
    sortedSub1[0]++;
  }
  else if (studentData[i].sub1 < 9) {
    sortedStudentDataSub1["5-8"]++;
    sortedSub1[1]++;
  }
  else if (studentData[i].sub1 < 13) {
    sortedStudentDataSub1["9-12"]++;
    sortedSub1[2]++;
  }
  else if (studentData[i].sub1 < 17) {
    sortedStudentDataSub1["13-16"]++;
    sortedSub1[3]++;
  }
  else{
    sortedStudentDataSub1["17-20"]++;
    sortedSub1[4]++;
  }

  if (studentData[i].sub2 < 5){
    sortedStudentDataSub2["0-4"]++;
    sortedSub2[0]++;
  }
  else if (studentData[i].sub2 < 9) {
    sortedStudentDataSub2["5-8"]++;
    sortedSub2[1]++;
  }
  else if (studentData[i].sub2 < 13) {
    sortedStudentDataSub2["9-12"]++;
    sortedSub2[2]++;
  }
  else if (studentData[i].sub2 < 17) {
    sortedStudentDataSub2["13-16"]++;
    sortedSub2[3]++;
  }
  else{
    sortedStudentDataSub2["17-20"]++;
    sortedSub2[4]++;
  }

  if (studentData[i].sub3 < 5){
    sortedStudentDataSub3["0 - 4"]++;
    sortedSub3[0]++;
  }
  else if (studentData[i].sub3 < 9) {
    sortedStudentDataSub3["5 - 8"]++;
    sortedSub3[1]++;
  }
  else if (studentData[i].sub3 < 13) {
    sortedStudentDataSub3["9 - 12"]++;
    sortedSub3[2]++;
  }
  else if (studentData[i].sub3 < 17) {
    sortedStudentDataSub3["13 - 16"]++;
    sortedSub3[3]++;
  }
  else{
    sortedStudentDataSub3["17 - 20"]++;
    sortedSub3[4]++;
  }
}
var sortedStudentData = [];
sortedStudentData.push(sortedStudentDataSub1);
sortedStudentData.push(sortedStudentDataSub2);
sortedStudentData.push(sortedStudentDataSub3);
var studentDataSub1 = [];
var studentDataSub2 = [];
var studentDataSub3 = [];
for (var i = 0; i < 50; i++){
  studentDataSub1.push(studentData[i].sub1);
  studentDataSub2.push(studentData[i].sub2);
  studentDataSub3.push(studentData[i].sub3)
}
console.log("studentData = ", studentData);
console.log("sortedStudentData", sortedStudentData);
console.log("sortedSub1", sortedSub1);
var compareLabel = ["0-4", "5-8", "9-12", "13-16", "17-20"];
var sortedObjectSub1 = [];
var sortedObjectSub2 = [];
var sortedObjectSub3 = [];
for (var i = 0; i < 5; i++){
  arr = {"label": compareLabel[i], "value": sortedSub1[i]};
  sortedObjectSub1.push(arr);
  arr = {"label": compareLabel[i], "value": sortedSub2[i]};
  sortedObjectSub2.push(arr);
  arr = {"label": compareLabel[i], "value": sortedSub3[i]};
  sortedObjectSub3.push(arr);
}
console.log("sortedObjectSub1", sortedObjectSub1);

var subjectDisplay = studentDataSub1;
var compareDisplay = sortedObjectSub1;

$(document).ready( function(){
  $(document).on('change','#subject-select-box',function(){
    var selectedVal = $( "#subject-select-box option:selected" ).text();
    if (selectedVal === "G1"){
      console.log("sub1");
      subjectDisplay = studentDataSub1;
      // compareDisplay = sortedSub1;
      compareDisplay = sortedObjectSub1;
      d3.selectAll("svg").remove();
      graphDisplay(subjectDisplay, compareDisplay);
    }
    if (selectedVal === "G3"){
      console.log("sub2");
      subjectDisplay = studentDataSub2;
      console.log(subjectDisplay)
      compareDisplay = sortedObjectSub2;
      d3.selectAll("svg").remove();
      graph2Display(subjectDisplay, compareDisplay);
      document.getElementById("content1").innerHTML = "This is the second Graph which is about how what the correlation between parents jobs and stuends grades."
      document.getElementById("content2").innerHTML = "We use 300 stuends grades in threee exams,and get the average grades of each parents jobs . The yellow is show Mother's job,and blue is fathers'job. And the yAxis is the students'grades in there exams.From left to the right: at_home;health;teacher;service;others.This graph show that if mother have better jobs or get higher education, the stuent will perform  better.<br>Medu - mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education)"+
        "<br>Fedu - father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education)"

    }
    if (selectedVal === "G2"){
      subjectDisplay = studentDataSub3;
      compareDisplay = sortedObjectSub3;
      d3.selectAll("svg").remove();
      document.getElementById("content1").innerHTML = "The second scene presents the correlation between fathers jobs and student grades."
      document.getElementById("content2").innerHTML = "We use 300 student grades in three exams and get the average grades of students whose father work in different jobs. The green represents female students and blue represents male students. The y-axis represents the student grades in exams and the x-axis represents father occupation. The radius of the circle is the education level of their father. Bigger radius represents the father has received higher education than those with smaller radius. The parameters of this chart are: student grades, father occupation (at home, services, other, teacher, health), father level of education. When the user moves the mouse on a specific circle, that specific data item will be highlighted with annotations (for example, StuGender, job of father, average score). It will be cleared as the mouse leaves. This graph shows that if father has better jobs or gets higher education, the student performs better in the exams."

      graph3Display(subjectDisplay, compareDisplay);
    }
  });
});

console.log(compareDisplay);
/////////////////////////////////////////////////////////////////////////////////
// Graph update function
////////////////////////////////////////////////////////////////////////////////
function graphDisplay(subjectDisplay, compareDisplay){

  var svgWidth = 650;
  var svgHeight = 400;
  var studentCanvas = d3.select(".practice-section").append("svg")
    .attr("width", svgWidth)
    .attr("height", svgHeight)
    .style("background", "#FFFDE7")
    .style("box-shadow", "1px 1px 6px 1px lightgray")
    .append("g")
      .attr("transform", "translate(30, -50)");

  console.log(studentDataSub1);
  var studentBarWidth = 10;
  var studentBarOffset = 2;
  var studentColorScale = d3.scaleLinear()
    .domain([0, d3.max(subjectDisplay)])
    .range(["#FFEB3B", "#00BCD4"]);
  var studentYScale = d3.scaleLinear()
    .domain([0, 20])
    .range([0, (svgHeight/2)]);
  var yAxisScale = d3.scaleLinear()
    .domain([0, 20])
    .range([svgHeight/2, 0]);
  var yAxis = d3.axisLeft(yAxisScale);
  var studentXScale = d3.scaleBand()
    .domain(d3.range(1, 51))
    .rangeRound([0, (svgWidth-30)]);
  var xAxis = d3.axisBottom(studentXScale);

  studentCanvas.selectAll("rect")
    .data(subjectDisplay)
    .enter()
    .append("rect")
      .attr("fill", function(d){ return studentColorScale(d); })
      .attr("width", studentBarWidth)
      .attr("height", function(d){ return studentYScale(d); })
      .attr("x", function(d, i){ return i* ( studentBarWidth + studentBarOffset ); })
      .attr("y", function(d){ return (svgHeight-studentYScale(d)); })
      .on("mouseover", function(d, i){
        console.log(3);
        tooltip.transition()
          .style("opacity", 1);
        tooltip.text("Student " + (i + 1) + " : " + d + " marks")
          .style("left", (d3.event.pageX + 15) + 'px')
          .style("top", (d3.event.pageY + 15) + 'px')
        d3.select(this)
          .style("opacity", ".5");
      })
      .append("text").text(function(d) { //添加文字描述
        return d;
      })
      .on("mouseout", function(d){
        tooltip.transition()
          .style("opacity", "0");
        d3.select(this)
          .style("opacity", "1");
      })
  studentCanvas.append("g")
    .attr("transform", "translate(0, 200)")
    .call(yAxis)
      .append("g")
      .append("text")
      .attr("transform", "translate(4, -40)")
      .attr("y", 20)
      .attr("dy", ".71em")
      .style("fill", "#000")
      .text("Marks");
  studentCanvas.append("g")
    .attr("transform", "translate(-10, 410)")
    .call(xAxis)
      .append("g")
      .append("text")
      .attr("dy", ".71em")
      .style("fill", "#000")
      .attr("transform", "translate(550, 25)")
      .text("Students");



  var tooltip = d3.select(".practice-section").append("section")
    .attr("class", "tooltip")
    .style("position", "absolute")
    .style("min-width", "30px")
    .style("background", "#f4f4f4")
    .style("padding", "5 15px")
    .style("border", "1px #333 solid")
    .style("border-radius", "1px")
    .style("opacity", "0")
    .style("padding", "2px")
    .style("text-align", "center")



  //////////////////////////////////////////////////////////////////////////////
  // second graph display
  //////////////////////////////////////////////////////////////////////////////
  var radius = svgHeight/2;

  //defining svg
  var compareCanvas = d3.select(".more-practice-section").append("svg")
  .attr("width", svgWidth)
  .attr("height", svgHeight)
  .style("background", "#FFFDE7")
  .style("box-shadow", "1px 1px 6px 1px lightgray")
  .append("g")
    .attr("transform", "translate(330, 200)");

  //arc generator
  var arc = d3.arc()
    .outerRadius(radius - 60)
    .innerRadius(radius - 100);

  //pie generator
  var pie = d3.pie()
    .sort(null)
    // .value(function(d) { return d; });
    .value(function(d) { return d.value; });

  var compareColorScale = d3.scaleLinear()
    .domain([0, 5])
    .range(["#E91E63", "#F8BBD0"]);

  var compareYLabel = ["0 - 20", "21 - 40", "41 - 60", "61 - 80", "81 - 100"];
  var theArc = compareCanvas.selectAll(".donut-arc")
    .data(pie(compareDisplay))
    // .data(pie(sortedObjectSub1))
    .enter()
    .append("g")
    .attr("class", "donut-arc");

  theArc.append("path")
    .attr("d", arc)
    .attr("fill", function(d, i){
      return compareColorScale(i);
    })
    .on("mouseover", function(d){
      tooltip.transition()
        .style("opacity", 1);
      // compareYLabel[i] + " : " + d
      tooltip.text( d.data.label + " : " + d.data.value)
        .style("left", (d3.event.pageX + 15) + 'px')
        .style("top", (d3.event.pageY + 15) + 'px')
      d3.select(this)
        .style("opacity", ".5");
        // console.log(d.data.label)
        // height = 240 ->20
        var myg = d3.selectAll("rect")._groups[0];
        switch (d.data.label) {
          case "0-4":
          console.log(myg[1].__data__);
          for(i=0;i<50;i++){

            if(myg[i].__data__<=4){
                myg[i].style.opacity= "0.5";
            }
          }
          break;
          case "5-8":
          for(i=0;i<50;i++){
            if(myg[i].__data__<=8 && myg[i].__data__>=5 ){
                myg[i].style.opacity= "0.5";
            }
          }
          break;

          case "9-12":
          for(i=0;i<50;i++){
            if(myg[i].__data__<=12 && myg[i].__data__>=9 ){
                myg[i].style.opacity= "0.5";
            }
          }
          break;

          case "13-16":
          for(i=0;i<50;i++){
            if(myg[i].__data__<=16 && myg[i].__data__>=13 ){
                myg[i].style.opacity= "0.5";
            }
          }
          break;
          case "17-20":
          for(i=0;i<50;i++){
            if(myg[i].__data__<=20 && myg[i].__data__>=17 ){
              myg[i].style.opacity= "0.5";
            }
          }
          break;

        }


    })
    .on("mouseout", function(d){
      tooltip.transition()
        .style("opacity", "0");
      d3.select(this)
        .style("opacity", "1");
        myg = d3.selectAll("rect")._groups[0];
        for(i=0;i<50;i++){
            myg[i].style.opacity= "1";
        }
    });

  // console.log("pie = ", pie(sortedObjectSub1));

  theArc.append("text")
    .attr("transform", function(d){
      return "translate(" + arc.centroid(d) + ")";
    })
    .attr("dy", "1.5em")
    .text(function(d) { return d.data.value; })
    .style("font-weight", "500")
    .style("font-size", "13px");
}

/////////////////
// Graph 2
////////////////
function graph2Display(subjectDisplay, compareDisplay){

  var svgWidth = 650;
  var svgHeight = 400;
  var studentCanvas = d3.select(".practice-section").append("svg")
    .attr("width", svgWidth)
    .attr("height", svgHeight)
    .style("background", "#FFFDE7")
    .style("box-shadow", "1px 1px 6px 1px lightgray")
    .append("g")
      .attr("transform", "translate(30, -50)");


  d3.csv("student-mat.csv",function(error,csvdata){
    if(error){
      console.log(error);
    }
    M_job=[0,0,0,0,0];//athome;health;teacher;service;others
    F_job=[0,0,0,0,0];
    M_count=[0,0,0,0,0];
    F_count=[0,0,0,0,0];
    len = csvdata.length;
    for( var i=0; i<len; i++ ){
       val = (parseInt(csvdata[i].G1)+parseInt(csvdata[i].G2)+parseInt(csvdata[i].G3) )/3;
       
       switch(csvdata[i].Mjob){
        case "at_home": M_job[0]+= val; M_count[0]++; break;
        case "health":  M_job[1]+= val;M_count[1]++;break;
        case "teacher":  M_job[2]+= val;M_count[2]++;break;
        case "services": M_job[3]+= val;M_count[3]++;break;
        case "other":    M_job[4]+= val;M_count[4]++;break;
       }
       switch(csvdata[i].Fjob){
        case "at_home": F_job[0]+= val;F_count[0]++; break;
        case "health":  F_job[1]+= val;F_count[1]++;break;
        case "teacher": F_job[2]+= val;F_count[2]++;break;
        case "services": F_job[3]+= val;F_count[3]++;break;
        case "other":    F_job[4]+= val;F_count[4]++;break;
       }  
    }
    job_score=[]
    for(i=0;i<5;i++){
      M_job[i] = M_job[i]/M_count[i];
      F_job[i] = F_job[i]/F_count[i];
      job_score.push(M_job[i]);
      job_score.push(F_job[i]);
    }    
    console.log(M_job);
    console.log(job_score);

    var studentBarWidth = 40;
    var studentBarOffset = 10;
    var student2ColorScale = d3.scaleLinear()
      .domain([-1, 0])
      .range(["#FFEB3B", "#00BCD4"]);
    var studentYScale = d3.scaleLinear()
      .domain([0, 20])
      .range([0, (svgHeight/2)]);
    var yAxisScale = d3.scaleLinear()
      .domain([0, 20])
      .range([svgHeight/2, 0]);
    var yAxis = d3.axisLeft(yAxisScale);
    var studentXScale = d3.scaleBand()
      .rangeRound([0, (svgWidth-30)]);
    var xAxis = d3.axisBottom(studentXScale).ticks(5);

    var cou = 0;
    var ind = 0;
    studentCanvas.selectAll("rect")
    .data(job_score)
    .enter()
    .append("rect")
      .attr("fill", function(d){ cou = ~cou ; console.log(i); return student2ColorScale(cou); })
      .attr("width", studentBarWidth)
      .attr("height", function(d){ return studentYScale(d); })
      .attr("x", function(d, i){ return i* ( studentBarWidth + studentBarOffset ); })
      .attr("y", function(d){ return (svgHeight-studentYScale(d)); })
      .attr("ind", function(d){ return (ind++); })
      .on("mouseover", function(d, i){
        switch(i){
          case 0: job = "M_job:at_home";break;
          case 2:job ="M_job:health";  break;
          case 4:job ="M_job:teacher"; break;
          case 6:job ="M_job:services";break;
          case 8:job ="M_job:other";break;
          case 1: job ="F_job:at_home";break;
          case 3:job ="F_job:health";  break;
          case 5:job ="F_job:teacher"; break;
          case 7:job ="F_job:services";break;
          case 9:job ="F_job:other";break;
        }
        tooltip.transition()
          .style("opacity", 1);
        tooltip.text(job + "||average score:"+d)
          .style("left", (d3.event.pageX + 25) + 'px')
          .style("top", (d3.event.pageY + 25) + 'px')
        d3.select(this)
          .style("opacity", ".5");
       
      })
      .on("mouseout", function(d){
        tooltip.transition()
          .style("opacity", "0");
        d3.select(this)
          .style("opacity", "1");
      })
    studentCanvas.append("g")
    .attr("transform", "translate(0, 200)")
    .call(yAxis).append("text")
      .attr("transform", "rotate(-90)")
      .attr("y", 20)
      .attr("dy", ".71em")
      .style("color", "#999")
      .text("Grades");
    studentCanvas.append("g")
    .attr("transform", "translate(-10, 410)")
    .call(xAxis)


    var tooltip = d3.select(".practice-section").append("section")
    .attr("class", "tooltip")
    .style("position", "absolute")
    .style("min-width", "30px")
    .style("background", "#f4f4f4")
    .style("padding", "5 15px")
    .style("border", "1px #333 solid")
    .style("border-radius", "1px")
    .style("opacity", "0")
    .style("padding", "2px")
    .style("text-align", "center")

  /////////Graph 2
    dataS = [{x:"Medu_1",y:0},
              {x:"Fedu_1",y:0},
              {x:"Medu_2",y:0},
              {x:"Fedu_2",y:0},
              {x:"Medu_3",y:0},
              {x:"Fedu_3",y:0},
              {x:"Medu_4",y:0},
              {x:"Fedu_4",y:0}]
    countS= [0,0,0,0,0,0,0,0]

    for(i=0;i<csvdata.length;i++){
          var s = parseInt(csvdata[i].G1)+parseInt(csvdata[i].G2)+parseInt(csvdata[i].G3)
        switch(csvdata[i].Medu){
          case '1': dataS[0].y += s/3;
                    countS[0] ++;
                    break;
          case '2': dataS[2].y += s/3;
                    countS[2] ++;
                    break;
          case '3': dataS[4].y += s/3;
                    countS[4] ++;
                    break;
          case '4': dataS[6].y += s/3;
                    countS[6] ++;
                    break;
        }
        switch(csvdata[i].Fedu){
          case '1': dataS[1].y += s/3;
                    countS[1] ++;
                    break;
          case '2': dataS[3].y += s/3;
                    countS[3] ++;
                    break;
          case '3': dataS[5].y += s/3;
                    countS[5] ++;
                    break;
          case '4': dataS[7].y += s/3;
                    countS[7] ++;
                    break;
        }

    }
    for(i=0;i<8;i++){
      dataS[i].y = dataS[i].y / countS[i];
    }

    console.log(dataS);

  //defining svg
  var compareCanvas = d3.select(".more-practice-section").append("svg")
  .attr("width", svgWidth)
  .attr("height", svgHeight)
  .style("background", "#FFFDE7")
  .style("box-shadow", "1px 1px 6px 1px lightgray")
  .append("g")
    .attr("transform", "translate(80, -50)");

    var studentBarWidth = 40;
    var studentBarOffset = 10;
    var student2ColorScale = d3.scaleLinear()
      .domain([-1, 0])
      .range(["#FFEB3B", "#00BCD4"]);
    var studentYScale = d3.scaleLinear()
      .domain([0, 20])
      .range([0, (svgHeight/2)]);
    var yAxisScale = d3.scaleLinear()
      .domain([0, 20])
      .range([svgHeight/2, 0]);
    var yAxis = d3.axisLeft(yAxisScale);
    var studentXScale = d3.scaleBand()
      .rangeRound([0, (svgWidth-30)]);
    var xAxis = d3.axisBottom(studentXScale).ticks(5);

    var cou = 0;
    var ind = 0;
    compareCanvas.selectAll("rect")
    .data(dataS)
    .enter()
    .append("rect")
      .attr("fill", function(d){ cou = ~cou ; return student2ColorScale(cou); })
      .attr("width", studentBarWidth)
      .attr("height", function(d){ return studentYScale(d.y); })
      .attr("x", function(d, i){ return i* ( studentBarWidth + studentBarOffset ); })
      .attr("y", function(d){ return (svgHeight-studentYScale(d.y)); })
      .attr("ind", function(d){ return (ind++); })
      .on("mouseover", function(d, i){
        
        tooltip.transition()
          .style("opacity", 1);
        tooltip.text(d.x+"[average score:"+d.y+"]")
          .style("left", (d3.event.pageX + 25) + 'px')
          .style("top", (d3.event.pageY + 25) + 'px')
        d3.select(this)
          .style("opacity", ".5");
       
      })
      .on("mouseout", function(d){
        tooltip.transition()
          .style("opacity", "0");
        d3.select(this)
          .style("opacity", "1");
      })
    compareCanvas.append("g")
    .attr("transform", "translate(0, 200)")
    .call(yAxis).append("text")
      .attr("transform", "rotate(-90)")
      .attr("y", 20)
      .attr("dy", ".71em")
      .style("color", "#999")
      .text("Grades");
    compareCanvas.append("g")
    .attr("transform", "translate(-10, 410)")
    .call(xAxis)

    var tooltip = d3.select(".practice-section").append("section")
    .attr("class", "tooltip")
    .style("position", "absolute")
    .style("min-width", "30px")
    .style("background", "#f4f4f4")
    .style("padding", "5 15px")
    .style("border", "1px #333 solid")
    .style("border-radius", "1px")
    .style("opacity", "0")
    .style("padding", "2px")
    .style("text-align", "center")

  });
  

  
}

function graph3Display(subjectDisplay, compareDisplay){
 var svgWidth = 650;
  var svgHeight = 400;
  var bubbleCanvas = d3.select(".practice-section").append("svg")
    .attr("width", svgWidth)
    .attr("height", svgHeight)
    .style("background", "#FFFDE7")
    .style("box-shadow", "1px 1px 6px 1px lightgray")
    .append("g")
      .attr("transform", "translate(30, -50)");

   function getX(jobname){
      switch(jobname){
        case "at_home": return 1; break;
        case "services": return 2; break;
        case "other": return 3; break;
        case "teacher": return 4; break;
        case "health": return 5; break;
      }
  }

  d3.csv("student-mat.csv",function(error,csvdata){
    if(error){
      console.log(error);
    }
    len = csvdata.length;
    var dataset = [];
    for( var i=0; i<len; i++ ){
      var item = {}
       val = (parseInt(csvdata[i].G1)+parseInt(csvdata[i].G2)+parseInt(csvdata[i].G3) )/3;
       item.x = getX(csvdata[i].Mjob);
       item.y = val;
       item.job = csvdata[i].Mjob;
       item.sex = csvdata[i].sex;
       item.parents = "Mother";
       item.r = parseInt(csvdata[i].Medu);
       dataset.push(item);

       item.x = getX(csvdata[i].Fjob);
       item.job = csvdata[i].Fjob;
       item.parents = "Father";
       item.sex = csvdata[i].sex;
       item.r = parseInt(csvdata[i].Fedu);

       dataset.push(item);
    }

    // x.domain(data.map(function(d) { return d.name; }));
    // y.domain([0, d3.max(data, function(d) { return d.end; })]);
    // console.log(getX(csvdata[1].Mjob));
    // console.log(dataset);

    var xScale = d3.scaleLinear()
    .domain([0, 6])
    .rangeRound([0, (svgWidth-30)]);

    var yScale = d3.scaleLinear()
   .domain([0, 20])
   .range([svgHeight/2, 0]);

    var xAxis = d3.axisBottom()
    .ticks(6)
   .scale(xScale);
    
    var yAxis = d3.axisLeft()
   .scale(yScale);

    bubbleCanvas.append('g')
   .attr('class', 'axis')
   .attr('transform',"translate(0, 200)")
   .call(yAxis)
      .append("g")
      .attr("transform", "translate(20, -40)")
      .append("text")
      .attr("y", 20)
      .attr("dy", ".71em")
      .style("fill", "#000")
      .text("Grades");;

    bl = "````````````````````````"
    bubbleCanvas.append('g')
   .attr('class', 'axis')
   .attr("transform", "translate(10, 410)")
   .call(xAxis)
      .append("g")
      .attr("transform", "translate(300, 0)")
      .append("text")
      .attr("y", 20)
      .attr("dy", ".71em")
      .style("fill", "#000")
      .text("Jobs:athome"+"```````````````"+" services"+bl+" other "+bl+"teacher"+bl+"health");;



    bubbleCanvas.selectAll('.point')
   .data(dataset)
   .enter()
   .append('circle')
   .attr('transform',"translate(10, 200)")
   .attr('class', 'point')
   .attr('fill', function(d) {
      if(d.parents == "Mother" ){
        if(d.sex =="M") {
          return 'crimson';
        }else{
          return '#2ec7c9';
        }
      } 
      else{
        if(d.sex =="F") {
          return 'green';
        }else{
          return 'steelblue';
        }
      }
   })
   .attr('fill-opacity', '0.1')
   .attr('cx', function(d) {
    return xScale(d.x);
   })
   .attr('cy', function(d) {
    return yScale(d.y);
   })
   .attr('r', function(d) {
    return (d.r*3);
   })
    .on("mouseover", function(d, i){
        tooltip.transition()
          .style("opacity", 1);
        tooltip.text("StuGender:"+d.sex + "  ||Job of"+d.parents+"  ||average score:"+d.y)
          .style("left", (d3.event.pageX + 25) + 'px')
          .style("top", (d3.event.pageY + 25) + 'px')
        d3.select(this)
          .style("opacity", ".8");
       
      })
      .on("mouseout", function(d){
        tooltip.transition()
          .style("opacity", "0");
        d3.select(this)
          .style("opacity", "1");
      });

    var tooltip = d3.select(".practice-section").append("section")
    .attr("class", "tooltip")
    .style("position", "absolute")
    .style("min-width", "30px")
    .style("background", "#f4f4f4")
    .style("padding", "5 15px")
    .style("border", "1px #333 solid")
    .style("border-radius", "1px")
    .style("opacity", "0")
    .style("padding", "2px")
    .style("text-align", "center");

  });
}



graphDisplay(subjectDisplay, compareDisplay);
