<html lang="en" dir="ltr">

<head>
  <meta charset="utf-8">
  <title>REPLUS TEST SITE</title>
</head>

<body>

  <h1>#StayHome</h1>
  <p><strong>Page 02</strong></p>

    <script>
    document.write("집에만 있는 당신에게 필요한 것들을 제공하는 홈페이지입니다. <br>");
    </script>
    <ul>
      <li> <a href="html_001.html"> 페이지 001 </a></li>
      <li> <a href="html_002.html"> 페이지 002 </a></li>
      <li> <a href="https://www.netflix.com/kr/"> 넷플릭스 사이트 </a> </li>
    </ul>
    <img src="하늘.jpg" width="300"  border="0" />
    
   
    <h1>새로고침할 때마다 숫자가 바뀝니다!</h1>
    /* 7.3절, 7.6절 */
    <hr>
    <script>
    var degrees=new Array();
    degrees[0]=Math.random()*100;
    degrees[1]=Math.random()*100;
    degrees[2]=Math.random()*100;
    var sum=0;
    for(i=0;I<degrees.length;i++)
      sum+=degrees[i];
    document.write("A=" + degrees[0] + "<br> B=" + degrees[1] + "<br> C=" +degrees[2] + "<br> A, B, C의 평균 값은" +sum/degrees.length + "<br>"); 
    </script>
    <br/>
    /* 7.3절, 7.6절 */
    
    <h1>7.4절 Date 객체 활용</h1>
    /*7.4절 "Date" 추가 */
    <script>
    var now=new Date();
    document.write("현재 시간 : " +now.toUTCString() + "<br><hr>");
    </script>
    <br/>
    /*7.4절 "Date" 추가 */

    <h1>예빈이와 가연이의 대화</h1>
    /*7.5절 String 객체 메소드 활용*/
    <script>
    var a=new String("오늘 여수로 놀러갈래?");
    var b=new String("난 집에 있는 게 더 좋아~ 놀러가면 부모님께서 걱정하셔.");
    
    document.write("예빈 : " +a+ "<br>");
    document.write("가연 : " +b+ "<br>");
    
    var sub=a.split(" ");
    document.write("예빈이의 말을 단어별로 나누면 : ");
    for(var i=0;i<sub.length; i++)
      document.write(sub[i] + "<br>");
    </script>
    <br />
    /*7.5절 String 객체 메소드 활용*/
    
    <hr /> <p>
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
