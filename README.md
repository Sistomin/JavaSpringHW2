Java Spring GB
Istomin Sergey group 6413



Задание: Используя Spring Boot, создайте простое веб-приложение, которое приветствует пользователя на главной странице.

1 Создаём новый проект на Spring Boot
через конструктор start.spring.io
выбранная зависемость Spring Web

![Image alt](https://github.com/Sistomin/JavaSpringHW2/blob/master/springIO.PNG)

2 выгружаем с сайта и разархивируем проект по нужной нам дериктории

3 открываем проект в IDE и редактируем класс MyFirstDemoProjectApplication:  

import org.springframework.boot.SpringApplication;  

import org.springframework.boot.autoconfigure.SpringBootApplication;  

import org.springframework.web.bind.annotation.GetMapping;  

import org.springframework.web.bind.annotation.RequestParam;  

import org.springframework.web.bind.annotation.RestController;  


@SpringBootApplication
@RestController
public class MyFirstDemoProjectApplication {

	public static void main(String[] args) {

		SpringApplication.run(MyFirstDemoProjectApplication.class, args);
	}
	@GetMapping("/hello")
	public String hello(@RequestParam(value = "name", defaultValue = "Sergey Istomin") String name) {
		return String.format("Hello, %s!", name);
	}
}
В начале кода мы импортируем несколько классов и аннотаций, облегчающих работу:
org.springframework.boot.SpringApplication — класс, который часто используется для загрузки и запуска приложений Spring;
org.springframework.boot.autoconfigure.SpringBootApplication — обозначает класс конфигурации, который объявляет один или несколько методов @Bean, а также запускает автоконфигурацию и сканирование компонентов в коде;
org.springframework.web.bind.annotation.GetMapping — аннотация для отображения результатов HTTP-запрос методом GET на определённые методы, функция которых — обрабатывать события;
org.springframework.web.bind.annotation.RequestParam — аннотация, указывающая, что параметр метода должен быть связан с параметром веб-запроса;
org.springframework.web.bind.annotation.RestController — удобная аннотация, которая сама аннотирована @Controller и @ResponseBody.

Аннотация @RestController сообщает Spring, что этот код описывает конечную точку, которая должна быть доступна через веб-интерфейс. Аннотация @GetMapping ("/hello") указывает Spring, что надо использовать указанный ниже метод hello() для ответа на запросы, отправленные на адрес http://localhost:8080/hello.

@RequestParam указывает Spring, что в запросе должно быть значение name, а если его там нет, то нужно использовать по значение по умолчанию defaultValue = "Sergey Istomin"

4 запускаем приложение 
![Image alt](https://github.com/Sistomin/JavaSpringHW2/blob/master/IDE.PNG)

5 Не завершая работу кода в IDE, откроем браузер и перейдём по адресу http://localhost:8080/hello.
На экране видим надпись
![Image alt](https://github.com/Sistomin/JavaSpringHW2/blob/master/HelloSergey.PNG)
 
или переходим по ссылке в браузире http://localhost:8080/hello?name=Igor
для указания имени которым попреветствовать
![Image alt](https://github.com/Sistomin/JavaSpringHW2/blob/master/Igor.PNG)
