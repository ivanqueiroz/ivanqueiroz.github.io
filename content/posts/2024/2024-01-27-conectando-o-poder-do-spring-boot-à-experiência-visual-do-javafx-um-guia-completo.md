---
title: "Integração Poderosa: Spring Boot + JavaFX"
description: ""
date: 2024-01-27T15:19:52.666Z
preview: ""
tags:
  [
    spring boot,
    javafx,
    java,
    desenvolvimento,
    programação,
    ui,
    aplicações desktop,
  ]
categories: [javafx, spring boot, java, programação, aplicações desktop]
---

Este artigo tem como objetivo mostrar como é possível combinar o Spring Boot e o JavaFx, permitindo a criação de aplicações desktop modernas e eficientes. O Spring Boot é um framework de injeção de dependência que permite a criação de aplicações Java de forma rápida e fácil. O JavaFx, por sua vez, é uma biblioteca gráfica para a criação de interfaces de usuário em Java. Para isso será mostrada uma aplicação de controle de tarefas utilizando Kanban.

> “_Trabalhar em equipe é a capacidade de trabalhar juntos em direção a uma visão comum_.”
>
> -- Andrew Carnegie

## Uma pequena explicação do que é JavaFX

![JavaFX](/images/2024/01/27/image.png)

O JavaFX representa uma plataforma de desenvolvimento para interfaces gráficas de usuário (GUI) em aplicativos destinados a desktops, dispositivos móveis e sistemas embarcados. Essa plataforma, construída com base no Java e de código aberto, capacita os desenvolvedores a conceber aplicativos sofisticados e interativos, dotados de recursos avançados em termos de gráficos, animação e multimídia{{< sup "1" >}}.

Em sua essência, o JavaFX representa uma evolução em relação ao Swing, que foi a biblioteca de GUI anteriormente oferecida pela Oracle. A proposta do JavaFX é proporcionar uma experiência de desenvolvimento mais acessível e robusta{{< sup "2" >}}. A sua relevância no âmbito do desenvolvimento de interfaces gráficas é destacada pela oferta de uma ampla gama de recursos, os quais possibilitam a criação de interfaces de usuário envolventes e dinâmicas. Entre esses recursos, incluem-se uma API dedicada a gráficos 2D e 3D, suporte para animações, efeitos visuais, implementação de folhas de estilo CSS, manipulação de áudio e vídeo, e compatibilidade com dispositivos de entrada como mouse, teclado e telas sensíveis ao toque{{< sup "1" >}}.

Vale ressaltar que o JavaFX adota um pipeline de gráficos, conhecido como Prism2, otimizado para o processamento de imagens, empregando, de forma interna, tecnologias como DirectX e OpenGL2 para uma eficiente aceleração gráfica, seja por meio de renderização por software ou hardware. Adicionalmente, o JavaFX integra uma camada de toolkit de janela Glass, dependente da plataforma, para uma interação fluida com o sistema operacional nativo, operando de modo assíncrono no gerenciamento de janelas, eventos e temporizadores{{< sup "2" >}}.

Adicionalmente, o JavaFX se destaca por sua alta customização e extensibilidade, conferindo aos desenvolvedores a capacidade de criar componentes personalizados e integrar-se facilmente com outras tecnologias Java, como o Java SE e o Java EE{{< sup "3" >}}.

O JavaFX, ao representar uma convergência de inovação e praticidade, emerge como uma ferramenta instrumental no panorama do desenvolvimento de interfaces gráficas. Sua propensão para a personalização e integração harmoniosa com tecnologias correlatas confirma sua posição proeminente no ecossistema Java, proporcionando aos desenvolvedores uma plataforma robusta e versátil para a materialização de suas visões criativas.

Aqui estão algumas das features do JavaFX:

- **FXML**: O FXML é uma linguagem de marcação baseada em XML para definir interfaces de usuário. Ele permite que os desenvolvedores criem interfaces de usuário sem escrever código Java{{< sup "2" >}}.
- **CSS**: O JavaFX suporta CSS para estilizar as interfaces de usuário. Ele permite que os desenvolvedores alterem a aparência dos componentes da interface do usuário, como botões, caixas de texto, etc.{{< sup "3" >}}.
- **Gráficos**: O JavaFX fornece suporte para gráficos 2D e 3D. Ele permite que os desenvolvedores criem gráficos personalizados, como gráficos de pizza, gráficos de barras, etc.{{< sup "3" >}}.
- **Multimídia**: O JavaFX suporta a reprodução de áudio e vídeo. Ele permite que os desenvolvedores criem aplicativos multimídia, como players de música, players de vídeo, etc.{{< sup "3" >}}.
- **Controles**: O JavaFX fornece uma ampla variedade de controles de interface do usuário, como botões, caixas de texto, tabelas, etc. Ele permite que os desenvolvedores criem interfaces de usuário ricas e interativas{{< sup "4" >}}.

## E o Spring Boot ?

![Spring Boot](/images/2024/01/27/spring_boot_logo.png)

O Spring Boot, um framework de código aberto fundamentado em Java, simplifica sobremaneira o desenvolvimento e a implementação de aplicações web. Como extensão do Spring Framework, que se destaca por oferecer uma plataforma abrangente voltada para o desenvolvimento de aplicações Java empresariais, o Spring Boot é notável por sua capacidade de simplificar a configuração e personalização das aplicações.

Este framework inovador aprimora o processo de desenvolvimento de aplicações web de diversas maneiras, abrindo mão da necessidade de criar arquivos XML de configuração. Em vez disso, utiliza propriedades ou anotações para definir os beans e as dependências do Spring. A inteligência embutida do Spring Boot detecta bibliotecas disponíveis no classpath, configurando-as de maneira astuta para evitar conflitos e redundâncias{{< sup "5" >}}.

A notável característica que permite a execução da aplicação como um jar executável, dispensando a necessidade de um servidor web externo, como o Tomcat ou o Jetty, destaca-se como uma das vantagens distintivas do Spring Boot. Adicionalmente, a presença de uma variedade de iniciadores (starters) facilita a integração com outras tecnologias, abrangendo bancos de dados, segurança, cache, web services, testes, entre outras áreas.

Um recurso de destaque é a ferramenta web conhecida como [Spring Initializr](https://start.spring.io/), que possibilita a geração rápida e fácil de um projeto Spring Boot com as dependências e configurações desejadas. Complementando isso, o Spring Boot incorpora recursos prontos para produção, incluindo métricas, verificações de saúde, configuração externa, logs, atuadores, entre outros.

Ao adotar o Spring Boot, os desenvolvedores podem direcionar seu foco para a lógica de negócio da aplicação, sem se deter nos pormenores da infraestrutura e configuração. Além disso, o Spring Boot viabiliza a criação descomplicada de aplicações baseadas em microsserviços, uma abordagem que favorece a implementação de pequenos serviços independentes que se comunicam harmonicamente, ampliando assim a escalabilidade, resiliência e flexibilidade das aplicações{{< sup "6" >}}.

## Uma aplicação Kanban para desktop

Durante as minhas férias comecei a organizar alguns projetos pessoais e veio na minha mente como seria criar uma aplicação de controle de tarefas que utilizasse Kanban. Eu sei que existem muitas aplicações disponíveis, mas a ideia era entender os desafios de criar um programa desses e também experimentar tecnologias, não querendo ser muito radical e ir para algo muito fora do Java (afinal estava de férias) e decidi revisitar o JavaFX por ser uma tecnologia que me atraiu muito na revisão para o Java 8, e por sempre ter uma preferência por desenvolvimento desktop.

A aplicação deveria ser simples e teria apenas o básico, permitindo criar, recuperar e excluir cards no board. Além do básico outra funcionalidade importante seria arrastar o card e alterar o status do mesmo, tendo um controle maior do andamento da tarefa. Toda a interface seria em JavaFX, possibilitando a animação de drag and over, interface customizável e interoperabilidade etc. Mas além disso, gostaria de ter todas as facilidades do Spring Boot para controle de injeção de dependência, conexão com banco de dados, agendar jobs etc.

## Modelagem do negócio

A modelagem da aplicação ficou bem simples e tem muito espaço para evoluir, mas basicamente ficou as representações de board, columns, tasks e o status das tasks:

![Diagrama de classe](/images/2024/01/27/diagrama_classe.png)

Para manter simples, o board terá apenas 3 colunas e cada coluna poderá ter várias tarefas.

## Configuração

Para o projeto foi utilizado o [Spring Initializr](https://start.spring.io/) para iniciar as configurações.

1. Estou utilizando o Java 17 para esse projeto, mas acredito que não teria problema utilizar uma versão mais recente.
2. Inicialmente não foi escolhido nenhum _starter_ do Spring, eles foram sendo adicionados a medida que as necessidades foram aparecendo.
3. Para facilitar a utilização do JavaFX esse não será um projeto que utilizará a configuração de módulos (Java 9), comum em projetos desktop em JavaFX.

## Ajustando o Spring Boot para iniciar a aplicação JavaFX

Como a aplicação será desktop não será necessário subir uma aplicação web, então podemos ajustar a configuração no `application.properties`:

```terminal
spring.main.web-application-type=none
```

### Classe que representa o aplicativo JavaFX

É necessário criar a classe que será responsável por iniciar a aplicação e que ela estenda javafx.application.Application:

```java
public class KanbanFxMainApplication extends Application {
  private ConfigurableApplicationContext applicationContext;
  @Override
  public void start(Stage stage) {
  }
}
```

Será necessário adicionar a dependência do JavaFX:

```xml
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-graphics</artifactId>
    <version>17</version>
</dependency>
```

### Ajuste na classe Application do Spring Boot

A classe criada precisa ser iniciada a partir do aplicativo Spring Boot.

Em vez de usar `org.springframework.boot.SpringApplication` para executar o aplicativo, usaremos a classe `javafx.application.Application` e chamaremos launch com a classe que é nossa classe JavaFX a `KanbanFxMainApplication` e passando os argumentos da aplicação.

```java
@EnableScheduling
@SpringBootApplication
public class SpringBootKanbanFxApplication {

  public static void main(String[] args) {
    Application.launch(KanbanFxMainApplication.class, args);
  }
}
```

Aqui uma observação: as duas classes são necessárias para poder trabalhar com JavaFX e Spring Boot juntos sem configurar os módulos do Java 9 (citado anteriormente), essa solução é uma forma de fazer funcionar os dois juntos.

### Configurando o contexto da aplicação

Para controlar o ciclo de vida da aplicação podemos publicar os eventos da mesma no contexto Spring. Para isso utilizamos `org.springframework.context.ConfigurableApplicationContext` e criamos os eventos da aplicação JavaFX:

Sobrepondo o método `start()`:

```java
public class KanbanFxMainApplication extends Application {
  private ConfigurableApplicationContext applicationContext;

  @Override
  public void start(Stage stage) {
    applicationContext.publishEvent(new StageReadyEvent(stage));
  }
}
```

O método start (de `Aplication` do JavaFX) é chamado com um objeto Stage quando está pronto para ser usado. Utilizando o padrão do Spring podemos publicar o evento que de quando a aplicação está pronta. O método `start(Stage stage)`, chama o `applicationContext.publishEvent()` com um novo `StageReadyEvent`, que é construído com o `Stage`.

Aqui está a classe `StageReadyEvent` que estende de `org.springframework.context.ApplicationEvent`:

```java
public class StageReadyEvent extends ApplicationEvent {
  public StageReadyEvent(Stage stage) {
    super(stage);
  }

  public Stage getStage() {
    return ((Stage) getSource());
  }
}
```

A inicialização do contexto é feita com a sobreposição do método `init()`, para ajudar utilizamos a classe `org.springframework.boot.builder.SpringApplicationBuilder` chamando o método `run()` com os argumentos:

```java
@Override
public void init() {
  applicationContext =
      new SpringApplicationBuilder(SpringBootKanbanFxApplication.class)
          .run(getParameters().getRaw().toArray(new String[0]));
}
```

Para encerrar o contexto, implementamos o método `stop()` completando a classe:

```java
  @Override
  public void stop() {
    applicationContext.close();
    Platform.exit();
  }
```

### Escutando os eventos da aplicação

Agora vamos implementar o _listerner_ para `StageReadyEvent`, para isso criamos a classe `StageReadyEventListener` que será anotada com `@Component` e implementará a interface `org.springframework.context.ApplicationListener`:

```java
@Component
@RequiredArgsConstructor
public class StageReadyEventListener implements ApplicationListener<StageReadyEvent> {

  @Value("${spring.application.ui.title}")
  private final String applicationTitle;

  @Override
  public void onApplicationEvent(StageReadyEvent event) {
    var stage = event.getStage();
  }
}
```

Agora já temos o básico da estrutura, mas para facilitar o desenvolvimento vamos fazer algumas modificações.

## Melhorando a injeção de dependência

No projeto vamos utilizar a lib [JavaFX-Weaver](https://github.com/rgielen/javafx-weaver) para melhorar a forma como a injeção das _views_ será realizada. O JavaFX-Weaver vincula uma classe controladora com o FXML utilizando o Spring como o DI, se quiser saber mais dê uma olhada nesse [artigo](https://rgielen.net/posts/2019/creating-a-spring-boot-javafx-application-with-fxweaver/). Utilizei ele nesse projeto para organizar melhor a estrutura das responsabilidades.

Para configurar basta seguir as instruções do site e adicionar a dependência do Maven:

```xml
<dependency>
    <groupId>net.rgielen</groupId>
    <artifactId>javafx-weaver-spring-boot-starter</artifactId>
    <version>1.3.0</version>
</dependency>
```

Agora ajustamos a classe `StageReadyEventListener`, passando a responsabilidade de carregar a view para a lib:

```java
  @Override
  public void onApplicationEvent(StageReadyEvent event) {
    var stage = event.getStage();
    Parent parent = fxWeaver.loadView(MainWindow.class);
    var scene = new Scene(parent);
    stage.setScene(scene);
    stage.setTitle(applicationTitle);
    stage.centerOnScreen();
    stage.show();
  }
```

A classe MainWindow é a janela principal do programa, ela é anotada com `@Component`, tornando-se um bean do Spring, bem como a anotação `@FxmlView`, que vincula a mesma ao `MainWindow.fxml`.

```java
@Slf4j
@FxmlView
@Component
@RequiredArgsConstructor
public class MainWindow {

    @FXML
    private MenuItem quitMenuItem;
    @FXML
    private BorderPane borderPane;
    private final BoardJavaFxAdapter boardJavaFxAdapter;
    private final ColumnJavaFxAdapter columnJavaFxAdapter;
    private final TaskJavaFxAdapter taskJavaFxAdapter;
    private final FxWeaver fxWeaver;
    private MultiColumnListView<TaskData> multiColumnListView;

    @FXML
    public void initialize() {
        initializeMenu();
        initializeBoard();
    }
    //métodos restantes
}
```

Coloquei aqui apenas o início da classe, onde já se pode usar as vantagens do DI do Spring que instancia todos os atributos finais pelo construtor (criado pelo `@RequiredArgsConstructor` do lombok).

## Recursos do Spring Boot utilizados

Com o Spring Boot configurado, foi possível utilizar o Spring Data com JPA para salvar dados no banco h2, agilizando muito o desenvolvimento e permitindo a utilização dos repositórios:

```java
//Entidade Board

@Entity
@Getter
@Setter
@AllArgsConstructor
@NoArgsConstructor
@Builder
@Table(name = "board")
public class BoardEntity {

  @Id
  @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "sequence_id_board")
  @SequenceGenerator(name = "sequence_id_board", sequenceName = "board_seq", allocationSize = 1)
  private Long id;

  private String name;
  private String description;

  @OneToMany(mappedBy = "board")
  private List<ColumnEntity> columns;
}
```

```java
//Repository da entidade Board

@Repository
public interface BoardRepository extends JpaRepository<BoardEntity, Long> {
  Optional<BoardEntity> findBoardEntityByNameEqualsIgnoreCase(String name);

  Optional<BoardEntity> findBoardEntityById(Long id);
}
```

Outra necessidade que surgiu na aplicação foi o de salvar o estado do board Kanban de tempos em tempos, para isso criei um job agendado com o `@Scheduled` do Spring Boot:

```java
  @Scheduled(fixedRate = 5000)
  public void saveBoard() {
    if (this.multiColumnListView != null) {
      this.multiColumnListView
          .getColumns()
          .forEach(
              taskDataListViewColumn -> {
                if (log.isDebugEnabled()) {
                  log.debug("Saving board");
                }
                var columnName =
                    ((Label) ((HBox) taskDataListViewColumn.getHeader()).getChildren().get(0))
                        .getText()
                        .toLowerCase();
                var columnData = columnJavaFxAdapter.getColumnByName(columnName).orElseThrow();
                columnData.setTasks(taskDataListViewColumn.getItems());
                columnJavaFxAdapter.save(columnData);
              });
    }
  }
```

## Conclusão

Esse artigo mostrou como configurar uma aplicação para unir o JavaFX com o Spring Boot, permitindo que o desenvolvimento desktop possa usufruir dos recursos de um dos frameworks mais utilizados no mercado, também foi apresentado alguns recursos que ajudaram no desenvolvimento da aplicação. Não foi objetivo mostrar detalhes da implementação da aplicação em si, mas se tiver curiosidade o código fonte desse projeto está [aqui no Github](https://github.com/ivanqueiroz/kanbanfx).

## Fontes

1. [Openjfx.io](https://openjfx.io/)
2. [Baeldung](https://www.baeldung.com/javafx)
3. [Oracle JavaFX CSS](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/doc-files/cssref.html)
4. [Oracle - JavaFX UI](https://docs.oracle.com/javase/8/javafx/user-interface-tutorial/ui_controls.htm)
5. [O que é Spring Boot? - Oracle DevLive](https://developer.oracle.com/pt-BR/learn/technical-articles/1482117195676-o-que-%C3%A9-spring-boot)
6. [Spring Boot: o que é e como usar: O guia inicial! - Blog da Trybe](https://blog.betrybe.com/framework-de-programacao/spring-boot-tudo-sobre/)
7. [Qual módulo de Spring você utiliza no desenvolvimento de aplicações?](https://coodesh.com/blog/candidates/backend/qual-modulo-de-spring-voce-utiliza-no-desenvolvimento-de-aplicacoes/)
8. [Tutorial: Reactive Spring Boot Part 3 – A JavaFX Spring Boot Application](https://blog.jetbrains.com/idea/2019/11/tutorial-reactive-spring-boot-a-javafx-spring-boot-application/)
9. [Creating a Spring Boot JavaFX Application with FxWeaver](https://rgielen.net/posts/2019/creating-a-spring-boot-javafx-application-with-fxweaver/)
