ViewPagerMultipleFragmentDemo
=============================

Multiple Fragments inside each tab of ViewPager with ViewPagerIndicator 

Install the apk file from /release folder to check the output 

## fragment

``` kotlin
  
  supportFragmentManager.beginTransaction().setReorderingAllowed(true).addToBackStack(null)
  .replae(R.id.container,Fragment()).commit()
```
   * Activity는 **supportFragmentManager 객체**로 내부의 Fragment들을 **Stack으로 관리**합니다.  
  Stack에는 전환할 떄 **addToBackStack (String tag) 함수**를 호출했을 경우에만 저장이 되어  
  **사용자가 Back버튼을 눌렀을 때 이전 Fragment가 보일 수 있도록 구현할 수 있습니다.**
  
  
## BackPressed

``` kotlin

  override func OnBackPressed(){
    super.onBackPressed()
  }
```
  

   * **OnBackPressed함수**는 사용자가 뒤로가기 버튼을 눌렀을 때, 호출되는 함수로,
   위 코드는 재정의하지 않았을 때의 코드이다.  
   **Fragment를 이용한 앱** 거기다가 **깊이를 가진 Fragment를 구현**하고 싶을 때에는  
   위 함수를 재정의 해주어야 한다.
   
  
``` kotlin
  
  override func OnBackPressed(){
    if( supportFragmentManager.backStackEntryCount >1){
        supportFragmentManager.popBackStackImmediate()
    }else{
        super.OnBackPressed()
    }
  }
```

  
    
   * **깊이가 있는 Fragment**는 뒤로가기 버튼을 사용자가 눌렀을 때, 이전 Fragment화면이 다시 불러와 지는 것입니다.  
   이 구현을 가능하게 해주는 이유가 **Fragment Stack**이 있기 때문인데요.  
   사용자가 뒤로가기 버튼을 눌렀을 때 **popBackStackImmediate()함수**를 호출 하여 이전 Fragment를 불러옵니다. 
