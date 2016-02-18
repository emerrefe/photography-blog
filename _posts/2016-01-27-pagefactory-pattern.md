---
layout: post
title: Patrón PageFactory (Selenium)
tags: java selenium patterns
eye_catch: ""
---

El patrón PageFactory se utiliza, junto con el patron Page Object a la hora de implementar pruebas funcionales
para hacer el código más mantenible y evitar escribir código como:

{% highlight java %}
WebElement searchInput = driver.findElement(By.xpath("//*[@id='twotabsearchtextbox']"));
{% endhighlight %}

De este modo, para hacer referencia a un elemento web, bastaría con importar:

{% highlight java %}
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;
{% endhighlight %}

Utilizar FindBy para tomar los elementos, así;

{% highlight java %}
@FindBy(xpath = "//*[@id='twotabsearchtextbox']")
private WebElement searchInput;
{% endhighlight %}

Inicializar esos elementos de la clase (u objeto de Page Object) con el PageFactory:
(hay que pasar el driver y la propia clase)

{% highlight java %}
public Search(WebDriver d2){
	driver = d2;  
	PageFactory.initElements(driver, this);
}
{% endhighlight %}

Y realizar operaciones sobre estos elementos en el método pertinente de la siguiente forma:

{% highlight java %}
public void searchString(String product){
	driver.get("https://www.amazon.com");	
	searchInput.sendKeys(product); //p.e enviar un string a ese input
}
{% endhighlight %}

Para tenerlo bien claro dejo por aquí la estructura del proyecto y las clases necesarias.
Por un lado estarán todas las clases u objetos (cada objeto del Page Object) y por otro las clases de los tests.

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/135417629@N05/22351998780/" title="Selección_123"><img src="https://farm1.staticflickr.com/609/22351998780_1121af3871.jpg" width="321" height="271" alt="Selección_123"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>


Clase "Buscador":
{% highlight java %}
package main;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;
import org.openqa.selenium.support.ui.WebDriverWait;

public class Search{
	
	public static WebDriverWait wait;
	public static WebDriver driver;
	
	//webElements
	@FindBy(xpath = "//*[@id='twotabsearchtextbox']")
	private WebElement searchInput;
	
	@FindBy(xpath = "//*[@id='nav-search']/form/div[2]/div/input")
	private WebElement searchButton;
    
    	public Search(WebDriver d2){
		driver = d2;  
		PageFactory.initElements(driver, this);
	}
    
	public void searchString(String product){
		driver.get("https://www.amazon.com");	
		searchInput.sendKeys(product);
		searchButton.click();
	}
}
{% endhighlight %}

Clase que contiene el test:
{% highlight java %}
package testsPaths;

import java.util.Arrays;

import main.Search;

import org.junit.AfterClass;
import org.junit.BeforeClass;
import org.junit.Test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;


public class TestExample {

	private static WebDriver driver;
	private static Search searchPage;
	
	private String product1 = "flowers"; 
	private String product2 = "mushrooms";
	
	@BeforeClass
	public static void setUp(){	
		System.setProperty("webdriver.chrome.driver", "src/chromedriver"); 	
		ChromeOptions options = new ChromeOptions();
		options.setExperimentalOption("excludeSwitches", Arrays.asList("ignore-certificate-errors"));
		driver = new ChromeDriver(options);  
		searchPage = new Search(driver); //inicializamos nuestro page object "buscador"
	}
		
	@AfterClass
	public static void tearDown(){
		driver.quit();
	}

	@Test
	public void testMethod() throws InterruptedException{
		searchPage.searchString(product1);
		searchPage.searchString(product2);
	}
}
{% endhighlight %}


¡Sed buenos!
