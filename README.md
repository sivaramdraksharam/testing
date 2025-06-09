Prerequisite: Annotations: https://github.com/sivaramdraksharam/Fullstack-Training/tree/8afda5c99334463fdbb7dd848a415b9094f6571e/mybuiltinannotations
# testing
Automation testing - screen recording guidelines

References:
1) download monte media jar from :
http://www.java2s.com/example/jar/m/download-montescreenrecorder0770jar-file.html#google_vignette

2) Refer to
   https://www.randelshofer.ch/monte/

Day-6
------
Topics
------
1. What is Monte? Monte is a media library used for screen recording using selenium webdriver.
2. Do we have Monte dependency in Maven Central? Yes. We need to include the dependency in pom.xml
program
------
1. Create a file called ScreenRecorderUtil.java
   import java.awt.AWTException;
import java.awt.Dimension;
import java.awt.GraphicsConfiguration;
import java.awt.GraphicsEnvironment;
import java.awt.Rectangle;
import java.awt.Toolkit;
import java.io.File;
import java.io.IOException;
import java.text.SimpleDateFormat;
import java.util.Date;

import org.monte.media.Format;
import org.monte.media.FormatKeys.MediaType;
import org.monte.media.Registry;
import org.monte.media.math.Rational;
import org.monte.screenrecorder.ScreenRecorder;

import static org.monte.media.AudioFormatKeys.*;
import static org.monte.media.VideoFormatKeys.*;

public class MyScreenRecorder extends ScreenRecorder {
	public static ScreenRecorder screenRecorder;
	public String name;

	public MyScreenRecorder(GraphicsConfiguration cfg, Rectangle captureArea, Format fileFormat,
			Format screenFormat, Format mouseFormat, Format audioFormat, File movieFolder, String name)
					throws IOException, AWTException {
		super(cfg, captureArea, fileFormat, screenFormat, mouseFormat, audioFormat, movieFolder);
		this.name = name;

	}

	@Override
	protected File createMovieFile(Format fileFormat) throws IOException {

		if (!movieFolder.exists()) {
			movieFolder.mkdirs();
		} else if (!movieFolder.isDirectory()) {
			throw new IOException("\"" + movieFolder + "\" is not a directory.");
		}
		SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH.mm.ss");
		return new File(movieFolder,
				name + "-" + dateFormat.format(new Date()) + "." + Registry.getInstance().getExtension(fileFormat));

	}

	public static void startRecording(String methodName) throws Exception {
		File file = new File("./recordings/");

		Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
		int width = screenSize.width;
		int height = screenSize.height;

		Rectangle captureSize = new Rectangle(0, 0, width, height);

		GraphicsConfiguration gc = GraphicsEnvironment.getLocalGraphicsEnvironment().
				getDefaultScreenDevice()
				.getDefaultConfiguration();

		screenRecorder = new MyScreenRecorder(gc, captureSize,
				new Format(MediaTypeKey, MediaType.FILE, MimeTypeKey, MIME_AVI),
				new Format(MediaTypeKey, MediaType.VIDEO, EncodingKey, ENCODING_AVI_TECHSMITH_SCREEN_CAPTURE,
						CompressorNameKey, ENCODING_AVI_TECHSMITH_SCREEN_CAPTURE, DepthKey, 24, FrameRateKey,
						Rational.valueOf(15), QualityKey, 1.0f, KeyFrameIntervalKey, 15 * 60),
				new Format(MediaTypeKey, MediaType.VIDEO, EncodingKey, "black", FrameRateKey, Rational.valueOf(30)),
				null, file, methodName);
		
		screenRecorder.start();

	}

	public static void stopRecording() throws Exception {
		screenRecorder.stop();
	}

}



----------------------------------
==================================
To test a simple web application using Selenium, you'll typically follow these steps:
1) Just call the startRecord("main") method from ScreenRecorderUtil class.
2) Set up Selenium WebDriver and a browser driver (like ChromeDriver for Chrome). 
3) Write a Selenium script in a programming language (e.g., Java, Python) to navigate to the web page, locate elements, and perform actions.
4) Run the script and verify the expected outcomes.
5) Stop recording test case by calling ScreenRecorderUtil.stopRecord(); //before quitting web driver
   
1. Prerequisites:
•	Selenium WebDriver:
Download and install Selenium WebDriver, which allows your script to control the browser. 
•	Browser Driver:
Download the appropriate browser driver for your chosen browser (e.g., ChromeDriver for Chrome, GeckoDriver for Firefox). Ensure the driver is compatible with your Selenium WebDriver version. 
•	Programming Language:
Choose a programming language (like Java, Python) and set up your development environment with the necessary libraries. 
2. Writing the Selenium Script:
•	Initialize WebDriver:
Create an instance of the desired browser driver (e.g., WebDriver driver = new ChromeDriver();).
•	Navigate to the Page:
Use the driver.get() method to navigate to the URL of the web application.
•	Locate Elements:
Identify and locate the web elements you need to interact with (e.g., input fields, buttons) using locators like id, name, xpath, or css_selector.
•	Perform Actions:
Use Selenium methods to interact with the elements (e.g., driver.findElement(By.id("username")).sendKeys("testuser") to enter text into a username field).
•	Verify and Validate:
Use assertions (e.g., assertEquals()) to verify that the application behaves as expected after each action. 
3. Running the Script:
•	Execute the Script:
Run your Selenium script using your programming language's environment (e.g., from an IDE or command line).
•	Inspect Results:
Observe the browser's behavior as the script executes. Check if the actions were performed correctly and if the expected outcomes are achieved. 
Example (Python):
Python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time
# Set up Chrome driver
driver = webdriver.Chrome()

# Navigate to the web page
driver.get("http://example.com")

# Locate an element
search_box = driver.find_element(By.ID, "search")

# Perform an action (e.g., type in the search box)
search_box.send_keys("Selenium tutorial")
search_box.send_keys(Keys.RETURN)

# Wait for the results to load
time.sleep(2)

# Verify that the results page is displayed
results = driver.find_elements(By.CSS_SELECTOR, "h3.r")
assert len(results) > 0

# Close the browser
driver.quit()
4. Best Practices:
•	Clear Code: Write clean, readable code that is easy to understand and maintain.
•	Locators: Use robust and reliable locators to identify elements.
•	Wait Strategically: Use Selenium waits to ensure elements are available before interacting with them.
•	Assertions: Use assertions to verify the expected behavior of the application. 




