<style>

/* a{
  margin-top:40vh;
  display:inline-block;
  text-decoration:none;
  color:rgba(0,0,0,1);
  -webkit-transition:color 0.25s; 
  transition:color 0.25s;
} */

a span{
  color:black;
  font-size:16px;
  
  position:absolute;
  top:10px;
  right:50%;
  margin-right:-430px;
  
  padding:50px 50px;
  
  border-style:solid;
  border-radius:175px;
  
  transform:scale(0);
  -webkit-transform:scale(0);
  
  transition:opacity 1s,transform 1.5s;
  -webkit-transition:opacity 1s, transform 1.5s;
  transition-delay: 0.5s;
  -webkit-transition-delay: 0.5s;
  
  opacity:0;
  

}
a div:hover ~span{opacity:1;  transform:scale(1);
  -webkit-transform:scale(1);}

/* a div
{
  cursor:pointer;
} */
</style>

<a href="/">
    <div>Hover Me</div>
    <span>
      This is a pop-up <!-- Put your text HERE-->
    </span>
    <!-- <svg height="130" width="200">
      <circle id='c1' cx="25" cy="55" r="5" stroke="black" stroke-width="3" fill="white" />
      <circle id='c2' cx="55" cy="35" r="8" stroke="black" stroke-width="3" fill="white" />
      <circle id='c3'  cx="85" cy="12" r="10" stroke="black" stroke-width="3" fill="white" />
    </svg> -->
  </a>
  
  