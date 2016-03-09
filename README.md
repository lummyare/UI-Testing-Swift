# UI Testing Helpers (Swift)
Helpers for UI Testing in Xcode 7 (Swift)

</br>

##Check existance of

###Static label 
	let application = XCUIApplication()
	let label = application.staticTexts["label-accessibilityIdentifier"]
	XCTAssertTrue(label.exists, "Message for assert failure")

    
###Image
    let application = XCUIApplication()
    let image = application.images["image-accessibilityIdentifier"]
    XCTAssertTrue(image.exists, "Message for assert failure")
       
    
###Button

    let application = XCUIApplication()
    let button = application.buttons["button-accessibilityIdentifier"]
    XCTAssertTrue(button.exists, "Message for assert failure")
    
###Navigation title

    let application = XCUIApplication()
    let navigationBar = application.navigationBars["navbar-title"]
    XCTAssertTrue(navigationBar.exists, "Message for assert failure")
    
    
 </br>  
 </br>  
 
 
  
##Timing
    
###Wait for element to load
	let element = ...
	let kTimeoutSeconds = 10.0 // test fails after 
	let predicate = NSPredicate(format: "exists == true")
	expectationForPredicate(predicate, evaluatedWithObject:element, handler: nil)
	waitForExpectationsWithTimeout(kTimeoutSeconds, handler: nil)



###Wait for specified time interval

	extension XCTestCase {
	
		func waitForTimeInterval(interval:NSTimeInterval) -> Void {   
		    let kTimeoutSeconds = ... // seconds before test fails, should be > interval
		    let expectation = expectationWithDescription("Expectation")
		    let delayTime = dispatch_time(DISPATCH_TIME_NOW, Int64(interval * Double(NSEC_PER_SEC)))
		    dispatch_after(delayTime, dispatch_get_main_queue()) {
		        expectation.fulfill()
		    }
		    waitForExpectationsWithTimeout(kTimeoutSeconds, handler: nil)
		}
	}
	
</br>

##Swipe

Swipe gestures which can be used with scrollView based elements 

###Up
       let scrollView = // scrollView based element
       scrollView.swipeUp()
       
###Down
       let scrollView = // scrollView based element
       scrollView.swipeDown()
       
###Left
       let scrollView = // scrollView based element
       scrollView.swipeLeft()
       
###Right
       let scrollView = // scrollView based element
       scrollView.swipeRight()