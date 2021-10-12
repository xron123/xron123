package Tetsleaf.SeleiumLearning;

import org.openqa.selenium.By;
import org.openqa.selenium.Dimension;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

import io.github.bonigarcia.wdm.WebDriverManager;

public class Trial {

	public static void main(String[] args) throws InterruptedException {
		
		WebDriverManager.chromedriver().setup();
        ChromeDriver driver = new ChromeDriver();
        
        driver.get( "http://leaftaps.com/opentaps/control/login");
        WebElement UID = driver.findElement(By.id("username"));
        WebElement PWD = driver.findElement(By.id("password"));
        WebElement LoginBtn = driver.findElement(By.className("decorativeSubmit"));
        		Thread.sleep(2000);
        UID.sendKeys("demosalesmanager");
    	Thread.sleep(2000);
        PWD.sendKeys("crmsfa");
        LoginBtn.click();
        driver.findElement(By.linkText("CRM/SFA")).click();
        Thread.sleep(2000);
        
        driver.findElement(By.linkText("Create Lead")).click();
        driver.findElement(By.id("createLeadForm_companyName")).sendKeys("TATA");
        driver.findElement(By.id("createLeadForm_firstName")).sendKeys("Tahir");
        driver.findElement(By.id("createLeadForm_lastName")).sendKeys("KP");
        driver.findElement(By.id("createLeadForm_firstNameLocal")).sendKeys("Taz");
        driver.findElement(By.id("createLeadForm_personalTitle")).sendKeys("Mr");
        driver.findElement(By.id("createLeadForm_generalProfTitle")).sendKeys("TL");
        driver.findElement(By.id("createLeadForm_annualRevenue")).sendKeys("52000");
        driver.findElement(By.id("createLeadForm_sicCode")).sendKeys("XYZ-234");
        driver.findElement(By.id("createLeadForm_description")).sendKeys("Hello Test");
        driver.findElement(By.id("createLeadForm_importantNote")).sendKeys(" Test note");
        driver.findElement(By.id("createLeadForm_primaryPhoneCountryCode")).clear();
        driver.findElement(By.id("createLeadForm_primaryPhoneCountryCode")).sendKeys("971");
        driver.findElement(By.id("createLeadForm_primaryPhoneAreaCode")).sendKeys("04");
        driver.findElement(By.id("createLeadForm_primaryPhoneExtension")).sendKeys("723");
        driver.findElement(By.id("createLeadForm_primaryPhoneNumber")).sendKeys("055607");
        driver.findElement(By.id("createLeadForm_primaryWebUrl")).sendKeys("www.linkedin.com");
     WebElement Countrylocation =  driver.findElement(By.id("createLeadForm_generalCountryGeoId"));
     Thread.sleep(2000);
     Select country = new Select(Countrylocation);
     Thread.sleep(2000);
     country.selectByVisibleText("Germany");
        driver.findElement(By.name("submitButton")).click();
        Thread.sleep(3000);
        String FirstName = driver.findElement(By.id("viewLead_firstName_sp")).getText();
        System.out.println(FirstName);
        
        String Current_tittle =  driver.getTitle();
        System.out.println("Current tittle is :" + Current_tittle);
          String expected_tittle = "View Lead ";
          if (Current_tittle.contains("View Lead"))
          {
			
		System.out.println("Tittle test passed");
		
          }
		else 
		{
			System.out.println("Tittle test failed");
		}
	}

}
