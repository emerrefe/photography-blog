---
layout: post
comments: True
title: Proyecto básico utilizando Selenium
tags: selenium
eye_catch: ""
---

Un ejemplo pequeño para empezar. Vamos a hacer una prueba sencilla.
Cargamos la web de amazon, introducimos una palabra y hacemos click en **Buscar** (icono de la lupa).

Herramientas que voy a utilizar:

- Eclipse, como entorno de desarrollo
- Java 1.8
- Selenium, con versiones 2.42
- Chrome como navegador, por tanto, Chrome driver, con versión 2.19

Para empezar, debemos descargar:

1. Los .zip, tanto del cliente como del servidor del [WebDriver](http://www.seleniumhq.org/download/)
2. El .zip del [web driver para Chrome](https://sites.google.com/a/chromium.org/chromedriver/downloads)

Procedemos:

1. Crear un nuevo proyecto Java en Eclipse, por ejemplo **FirstSelenimProject**
2. Incluir en el **src/** de ese proyecto tanto el chrome-driver como los .jar correspondientes a cliente y servidor de web-driver, es decir, el .jar de **selenium-server-standalone-java-X.jar** y  extraer el contenido de **selenium-java-X.zip**.
3. Crear una nueva clase .java con el siguiente contenido:

{% highlight java %}
import java.util.Arrays;

import org.junit.AfterClass;
import org.junit.BeforeClass;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class TestExample {
	
	public static WebDriver driver;
	
	@BeforeClass
	public static void setUp(){
		System.setProperty("webdriver.chrome.driver", "src/chromedriver"); 
		
		ChromeOptions options = new ChromeOptions();
	    	options.setExperimentalOption("excludeSwitches", Arrays.asList("ignore-certificate-errors"));
		driver = new ChromeDriver(options);            
	}

	@AfterClass
	public static void tearDown(){
		driver.quit();
	}

	@Test
	public void testMethod() throws InterruptedException{
		driver.get("https://www.amazon.com");
		WebElement searchInput;
		WebElement searchButton;

		searchInput = driver.findElement(By.xpath("//*[@id='twotabsearchtextbox']"));
		searchButton = driver.findElement(By.xpath("//*[@id='nav-search']/form/div[2]/div/input"));
			
		searchInput.sendKeys("flores");
		searchButton.click();
	}
}
{% endhighlight %}

Tras ejecutar la clase, se observa que se abre una ventana nueva de Chrome y comienza a hacer los pasos que le hemos indicado en el test.

Pues bien, con esto ya sabemos cómo lanzar pruebas contra nuestro navegador, ahora sólo queda indagar para saber cómo utilizar todos los métodos que interaccionan con los elementos de la página.

En un nuevo post, comentaré de qué formas diferentes podemos identificar los elementos que aparecen en la web.

¡Espero que sea de ayuda! ;)
