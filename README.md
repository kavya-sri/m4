package selenium;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.firefox.FirefoxProfile;

public class M4 {
	public static void main(String[] args) throws InterruptedException 
	{
		System.setProperty("webdriver.firefox.bin",
				"C:/Users/gamsri/AppData/Local/Mozilla Firefox/firefox.exe");
        FirefoxProfile profile = new FirefoxProfile();
        profile.setPreference("network.proxy.type", 1);
        profile.setPreference("network.proxy.http", "10.219.96.26");
        profile.setPreference("network.proxy.http_port", 8080);
        profile.setPreference("network.proxy.ssl", "10.219.96.26");
        profile.setPreference("network.proxy.ssl_port", 8080);
        
        FirefoxDriver driver = new FirefoxDriver(profile);
        driver.get("http://demo.opencart.com");
		Thread.sleep(1000);
		
        System.out.println("Execution is stopped for 10 seconds");
		boolean title=driver.getTitle().contains("Your Store");
		if(title)
		{
			System.out.println("Title matches");
		}
		else
		{
			System.out.println("Title not matches");
		}
		
        System.out.println("Waiting for the page to load");
        driver.manage().timeouts().implicitlyWait(10,TimeUnit.SECONDS) ;
        java.util.List<WebElement> links = driver.findElements(By.tagName("a"));
        
        int expectedlinks=73;
		 
		int actuallinks=links.size();
		
		if(expectedlinks==actuallinks)
		{
			System.out.println("No of links are equal to expected links " +actuallinks);
		}
		else
		{
			System.out.println("No of links are npot equal to expected links" +actuallinks);	
		}
		driver.findElement(By.linkText("My Account")).click();
		Thread.sleep(1000);
		System.out.println("My Account is clicked");
		
		driver.findElement(By.linkText("Register")).click();
		//Thread.sleep(1000);
		System.out.println("Register is clicked");
		
		driver.findElement(By.name("firstname")).sendKeys("Kavya");
		WebElement fname = driver.findElement(By.name("firstname"));
		String name = fname.getAttribute("value");
		if(Validation.ValidateflName(name))
		{
			System.out.println("Valid fistname");
			driver.findElement(By.name("lastname")).sendKeys("Sri");
			Thread.sleep(1000);
			WebElement last = driver.findElement(By.name("lastname"));
			String name1 = last.getAttribute("value");
			if(Validation.ValidateflName(name1))
			{
				System.out.println("valid Last name");			
				driver.findElement(By.name("email")).sendKeys("frlkl@gjfce.brgv");
				Thread.sleep(1000);
				WebElement email = driver.findElement(By.name("email"));
				String mail = email.getAttribute("value");
				if(Validation.Validatemail(mail))
				{
					System.out.println("valid email");
					driver.findElement(By.name("telephone")).sendKeys("8333940667");
					Thread.sleep(1000);
					WebElement phone = driver.findElement(By.name("telephone"));
					String number = phone.getAttribute("value");
					if(Validation.ValidateNumber(number))
					{
						System.out.println("valid phone number");
						driver.findElement(By.name("password")).sendKeys("kavya123");
						Thread.sleep(1000);
						WebElement pwd = driver.findElement(By.name("password"));
						String pass = pwd.getAttribute("value");
						driver.findElement(By.name("confirm")).sendKeys("kavya123");
						WebElement pwd1 = driver.findElement(By.name("confirm"));
						String pass1 = pwd1.getAttribute("value");
						if(pass.equals(pass1))
						{
							System.out.println("Password is matching");
						}
					}
					
				}
				
			}
		}
		driver.findElement(By.xpath(".//*[@id='content']/form/fieldset[3]/div/div/label[2]")).click();
		System.out.println("Clicked: No button");
		
		driver.findElement(By.name("agree")).click();
        driver.findElement(By.cssSelector("input[value='Continue']")).click();
		
		Thread.sleep(1500);
		boolean text4=driver.getPageSource().contains("Your Account Has Been Created!");
		if(text4)
		{
			System.out.println("Your Account Has Been Created! is present");
		}
		else
		{
			System.out.println("Your Account Has Been Created! is not present");
		}
		Thread.sleep(1500);
		driver.findElement(By.linkText("Phones & PDAs")).click();
		driver.findElement(By.linkText("HTC Touch HD")).click();
		boolean text5=driver.getPageSource().contains("HTC Touch HD");
		if(text5)
		{
			System.out.println("HTC Touch HD is present");
		}
		else
		{
			System.out.println("HTC Touch HD is not present");
		}
		Thread.sleep(1500);
		driver.navigate().back();
		
		driver.findElement(By.xpath(".//*[@id='content']/div[2]/div[1]/div/div[2]/div[2]/button[1]")).click();
		System.out.println("Add to cart button is clicked");
		
		Thread.sleep(1500);
		boolean text6=driver.getPageSource().contains("Success: You have added HTC Touch HD to your shopping cart!");
		if(text6)
		{
			System.out.println("Success: You have added HTC Touch HD to your shopping cart! is present");
		}
		else
		{
			System.out.println("Success: You have added HTC Touch HD to your shopping cart! is not present");
		}
		Thread.sleep(1500);
		driver.findElement(By.linkText("Brands")).click();
		
		boolean title1=driver.getTitle().contains("Find Your Favorite Brand");
		if(title1)
		{
			System.out.println("Title matches");
		}
		else
		{
			System.out.println("Title not matches");
		}
		driver.findElement(By.linkText("Canon")).click();
		boolean text7=driver.getPageSource().contains("Canon");
		if(text7)
		{
			System.out.println("Canon is present");
		}
		else
		{
			System.out.println("Canon is not present");
		}
		
		driver.findElement(By.xpath(".//*[@id='content']/div[2]/div[1]/div/div[2]/div[2]/button[2]")).click();
		System.out.println("Clicked on add to wishlist icon");
		
		Thread.sleep(1000);
		boolean text8=driver.getPageSource().contains("Success: You have added Canon EOS 5D to your wish list!");
		if(text8)
		{
			System.out.println("Success: You have added Canon EOS 5D to your wish list! is present");
		}
		else
		{
			System.out.println("Success: You have added Canon EOS 5D to your wish list! is not present");
		}
		
		driver.findElement(By.linkText("Wish List (1)")).click();
		
		boolean title2=driver.getTitle().contains("My Wish List");
		if(title2)
		{
			System.out.println("Title matches");
		}
		else
		{
			System.out.println("Title not matches");
		}
		
		Thread.sleep(1500);
		
		driver.findElement(By.xpath(".//*[@id='content']/div[2]/div/a")).click();
		driver.close();
	}
}
