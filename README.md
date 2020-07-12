<html lang="en" dir="ltr">

<head>
 <meta charset="utf-8">
 <script>
                function startScroll(interval) {
                setInterval("autoscroll()", interval);
                }
                function autoScroll() {
                window.scrollBy(0, 10);
                }
  </script>
</head>
     // 10.4절 웹페이지 자동 스크롤 적용
      
                <body onload="startScroll(1000)">
                <h1>#StayHome</h1>
                <p><strong>Page 02</strong></p>
                
                <script>
                document.write("집에만 있는 당신에게 필요한 것들을 제공하는 홈페이지입니다. <br> 하단 이미지 클릭 시 다양한 풍경을 보여줍니다. <br> 이 페이지에는 자동으로 스크롤되는 기능이 있습니다.");
                </script>
                <ul>
                  <li> <a href="html_001.html"> 페이지 001 </a></li>
                  <li> <a href="html_002.html"> 페이지 002 </a></li>
                  <li> <a href="html_003.html"> 페이지 003 </a></li>
                  <li> <a href="https://www.netflix.com/kr/"> 넷플릭스 사이트 </a> </li>
                </ul>
                <script>
                var files=["하늘.jpg", "ocean.jpg", "desert.jpg", "forest.jpg"];
                var imgs=new Array();
                for(var i=0;i<files.length;i++){
                  imgs[i]=new Image();
                  imgs[i].src=files[i];
                  }
                                     var next=1;
                                     function change(img){
                                     img.src=imgs[next].src;
                                     next++;
                                     next %=imgs.length;
                                     }
                                     <img style="border:20px ridge wheat" src="하늘.jpg" alt="." width="200" height="200" onclick="change(this)">
                   </script>
                   // 9.5절 new Image()로 이미지 로딩과 출력 실행함. 7.3절 배열도 적용됨.
                   <br>
    
    <h1>새로고침할 때마다 숫자가 바뀝니다!</h1>
    // 7.3절, 7.6절[^2]
    <script>
    var degrees=new Array();
    degrees[0]=Math.random()*100;
    degrees[1]=Math.random()*100;
    degrees[2]=Math.random()*100;
    var sum=0;
    for(i=0;I<degrees.length;i++)
      sum+=degrees[i];
    </script>
    document.write("A=" + degrees[0] + "<br> B=" + degrees[1] + "<br> C=" +degrees[2] + "<br> A, B, C의 평균 값은" +sum/degrees.length + "<br>");
    <br/>
    // 
    
    <h1>7.4절 Date 객체 활용</h1>
    
    // 7.4절 "Date" 추가[^4]
    <script>
    var now=new Date();
    function init(){
      clock();
      setInterval(clock,1000);
      }
      function clock(){
        var now = new Date();
        var ctx = document.getElementById('canvas').getContext('2d');
        ctx.save();
        ctx.clearRect(0,0,150,150);
        ctx.translate(75,75);
        ctx.scale(0.4,0.4);
        ctx.rotate(-Math.PI/2);
        ctx.strokeStyle = "black";
        ctx.fillStyle = "white";
        ctx.lineWidth = 8;
        ctx.lineCap = "round";

        // 시계판 - 시
        ctx.save();
        for (var i=0;i<12;i++){
          ctx.beginPath();
          ctx.rotate(Math.PI/6);
          ctx.moveTo(100,0);
          ctx.lineTo(120,0);
          ctx.stroke();
        }
        ctx.restore();

        // 시계판 - 분
        ctx.save();
        ctx.lineWidth = 5;
        for (i=0;i<60;i++){
          if (i%5!=0) {
            ctx.beginPath();
            ctx.moveTo(117,0);
            ctx.lineTo(120,0);
            ctx.stroke();
          }
          ctx.rotate(Math.PI/30);
        }
        ctx.restore();
  
        var sec = now.getSeconds();
        var min = now.getMinutes();
        var hr  = now.getHours();
        hr = hr>=12 ? hr-12 : hr;

        ctx.fillStyle = "black";

        // 시간 표시 - 시
        ctx.save();
        ctx.rotate( hr*(Math.PI/6) + (Math.PI/360)*min + (Math.PI/21600)*sec )
        ctx.lineWidth = 14;
        ctx.beginPath();
        ctx.moveTo(-20,0);
        ctx.lineTo(80,0);
        ctx.stroke();
        ctx.restore();

        // 시간 표시 - 분
        ctx.save();
        ctx.rotate( (Math.PI/30)*min + (Math.PI/1800)*sec )
        ctx.lineWidth = 10;
        ctx.beginPath();
        ctx.moveTo(-28,0);
        ctx.lineTo(112,0);
        ctx.stroke();
        ctx.restore();
  
        // 시간 표시 - 초
        ctx.save();
        ctx.rotate(sec * Math.PI/30);
        ctx.strokeStyle = "#D40000";
        ctx.fillStyle = "#D40000";
        ctx.lineWidth = 6;
        ctx.beginPath();
        ctx.moveTo(-30,0);
        ctx.lineTo(83,0);
        ctx.stroke();
        ctx.beginPath();
        ctx.arc(0,0,10,0,Math.PI*2,true);
        ctx.fill();
        ctx.beginPath();
        ctx.arc(95,0,10,0,Math.PI*2,true);
        ctx.stroke();
        ctx.fillStyle = "rgba(0,0,0,0)";
        ctx.arc(0,0,3,0,Math.PI*2,true);
        ctx.fill();
        ctx.restore();

        ctx.beginPath();
        ctx.lineWidth = 14;
        ctx.strokeStyle = '#325FA2';
        ctx.arc(0,0,142,0,Math.PI*2,true);
        ctx.stroke();

        ctx.restore();
      }
      </script>
    document.write("현재 시간 : " +now.toUTCString() + "<br><hr>");
    <br/>
    
    // 7.4절 "Date" 추가[^5]
    
    //10.3절 setInterval() 이용하여 텍스트를 반복 회전시키는 코드
    
    <div><span id="span" style="background-color:aliceblue:>
    자동 회전하는 텍스트입니다.</span>
    </div>
    <script>
    var span=document.getElementById("span");
    var timerID=setInterval("doRotate()", 200);
    
    span.onclick=function(e) {
      clearInterval(timerID);
      }
      
      function doRotate() {
      var strr=span.innerHTML;
      var firstChar=strr.substr(0,1);
      var remaions=strr.substr(1, strr.length-1);
      strr=remains + firstChar;
      span.innerHTML = strr;
      }
      </script>
      
      <h1>예빈이와 재혁이와 가연이의 대화</h1>
      // 7.5절 String 객체 메소드 활용[^6]
      
      <script>
      var a=new String("오늘 여수로 놀러갈래?");
      var b=new String("난 집에 있는 게 더 좋아~ 놀러가면 부모님께서 걱정하셔.");
      var c=new String("그러니? 난 부산으로 놀러가고 싶다~");
      document.write("예빈 : " +a+ "<br>");
      document.write("가연 : " +b+ "<br>");
      document.write("재혁 : " +c+ "<br>");
      
      var sub=a.split(" ");
      document.write("예빈이의 말을 단어별로 나누면 : <br>");
      for(var i=0;i<sub.length; i++){
         document.write(sub[i] + "<br>");
         }
         </script>
         <br/>
         
         // 7.5절 String 객체 메소드 활용[^7]
         // 9.6절 선택된 라디오버튼 찾아 경고창에 출력하기[^9]
         
         <h1>당신은 어디로 놀러가고 싶으신가요?</h1>
         <script>
         function findChecked() {
            var found=null;
            var region=document.getElementsByName("kregion");
            for(var i=0;i<region.length;i++){
               if(region[i].checked==true)
                  found=region[i];
                  }
               if(found!=null)
                  alert(found.value + "이 선택되었음");
               else
                  alert("선택된 것이 없음");
                  }
                  </script>
                  <form>
                     <input type="radio" name="region" value="yeosoo" checked>여수
                     <input type="radio" name="region" value="home" checked>집
                     <input type="radio" name="region" value="busan" checked>부산
                     <input type="button" value="find checked" onclick="findChecked()">
                  </form>
                  <br>
                  // 9.6절 선택된 라디오버튼 찾아 경고창에 출력하기[^10]
                  
                  
                  <hr/> <p>
                  something important thing is missing in your life
                  </p>
                  
                  <form class="" action="index.html" method="post">
                     <label>yourname</label>
                  </form>

                  <form action="">
                     <label for="GET-name">Name:</label>
                     <input id="GET-name" type="text" name="name">
                     <input type="submit" value="Save">
                  </form>
                  <!-- Simple form which will send a POST request -->
                  <form action="" method="post">
                     <label for="POST-name">Name:</label>
                     <input id="POST-name" type="text" name="name">
                     <input type="submit" value="Save">
                  </form>

                  <!-- Form with fieldset, legend, and label -->
                  <form action="" method="post">
                     <fieldset>
                     <legend>Title</legend>
                     <input type="radio" name="radio" id="radio"> <label for="radio">Click me</label>
                     </fieldset>
                  </form>
                  
                  </body>
                  </html>
