# Progress Bar Sample Code
This is just simple sample code to make a circular progress bar on Android. Simple to impliment, yet can be modified to your 
use and liking.

##Use
Make a drawable file to be used for the progress bar.
````
<layer-list xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="180"
    android:pivotX="50%"
    android:pivotY="50%"
    android:toDegrees="180">
    <item android:id="@android:id/background">
        <shape
            android:innerRadiusRatio="3"
            android:shape="ring"
            android:useLevel="false"
            android:thicknessRatio="10.0">
            <corners android:radius="5dip" />
            <solid android:color="#000000"/>
        </shape>
    </item>
    <item android:id="@android:id/progress">
        <rotate
            android:fromDegrees="270"
            android:toDegrees="270">
            <shape
                android:innerRadiusRatio="3"
                android:shape="ring"
                android:type="sweep"
                android:thicknessRatio="10.0">
                <solid android:color="#64FFDA"/>
            </shape>
        </rotate>
    </item>
</layer-list>
````
After making this file, and inserting the code, you will get a simple circular progress bar that will rotate depending on the 
value that you have given it in this companion Java code:
````...
        animateBar();
    }
    public void animateBar() {

        new Thread(new Runnable() {
            public void run() {
                final int percent = 0;
                while (mProgressStatus < 80) {
                    mProgressStatus += 1;
                    // Update progress bar to 80%. Change 80% to whatever value or resource needed. //THIS IS THE VALUE 
                    mHandler.post(new Runnable() {
                        public void run() {
                           // progBar.setProgress(mProgressStatus);
                        }
                    });
                    try {
                        Thread.sleep(50);

                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }).start();
    }

````
In your Java file, make sure to call animateBar(); to initialize the animation of the bar.


