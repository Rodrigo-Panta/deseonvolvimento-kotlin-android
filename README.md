# Desenvolvimento Mobile com Kotlin e Android
Este repositório contém um aplicativo android desenvolvido com a IDE Android Studio utilizando o modelo Empty Activity. 

O objetivo desse roteiro é permitir que o usuário tenha o primeiro contato com a linguagem Kotlin e adquira noções de desenvolvimento android com essa linguagem.

O aplicativo **ToDoListApp** apresentado trata-se de uma simples lista de afazeres em que o usuário consegue inserir novas tarefas e marcá-las como feitas.

Nesse roteiro, será implementada uma maneira de excluir tarefas da lista que estejam marcadas como feitas.

## Introdução a linguagem
Em programas Kotlin, a função main() é o local específico do código em que o compilador Kotlin é iniciado. Em apps Android, a função onCreate() cumpre esse papel. A função onCreate() é o ponto de entrada do app e chama outras funções para criar a interface do usuário.

Observe abaixo a função **main()** de um projeto que faz um print na tela da frase *"Hello Android!"*

```kotlin
class MainActivity : ComponentActivity() {
   override fun onCreate(savedInstanceState: Bundle?) {
       super.onCreate(savedInstanceState)
       setContent {
           GreetingCardTheme {
               // A surface container using the 'background' color from the theme
               Surface(
                   modifier = Modifier.fillMaxSize(),
                   color = MaterialTheme.colors.background
               ) {
                   Greeting("Android")
               }
           }
       }
   }
}
```

Nesse código é possível observar as interações entre as funções **main()**, **onCreate()** e tmabém a função **setContent()**. A função **setContent()** na função **onCreate()** é usada para definir o layout usando funções de composição. Todas as funções marcadas com a anotação **@Composable** podem ser chamadas na função **setContent()** ou em outras funções de composição. A anotação diz ao compilador Kotlin que essa função é usada pelo Jetpack Compose para gerar a IU (Interface). Note que no caso desse projeto está sendo usado um modelo Compose diferente do modelo Empty Activity usado no projeto **ToDoListApp**, e o objetivo aqui é somente introduzir um pouco da linguagem kotlin para voçes.

Agora, observe a função **Greeting()**. A função **Greeting()** é de composição e, por esse motivo, a anotação **@Composable** aparece acima dela. Uma função de composição recebe uma entrada e gera o que vai ser mostrado na tela.

```kotlin
@Composable
fun Greeting(name: String) {
   Text(text = "Hello Android!")
}
```

Nesse caso, como dito anteriormente, será gerado na tela a frase *"Hello Android!"*.

No arquivo *MainActivity.kt* do projeto **ToDoListApp** encontrado em ```java -> com.example.todolistaap -> MainActivity``` é possível observar o funcionamento 
da função main() referente a esse projeto. É recomendado que voçe estude um pouco a função main() antes de seguir as atividades do roteiro para que consiga visualizar
melhor o que está acontecendo na execução do projeto.

## Parte 1: Instalação do projeto ToDoListApp
Primeiramente, é necessária a instalação do Android Studio. Instale uma versão igual ou superior a **2021.3.1 Patch 1**

Siga o passo a passo presente no link abaixo para o sistema operacional adequado:
https://developer.android.com/studio/install?hl=pt-br

Após a instalação do Android Studio, siga os seguintes passos:

1. Faça um fork do repositório clicando no botão **Fork** no canto superior direito.

2. No terminal, clone o projeto com o seguinte comando:

```
git clone https://github.com/<SEU USUÁRIO>/desenvolvimento-kotlin-android.git
```
3. Abra o Android Studio. Na tela inicial, clique em **Projects** na aba lateral esquerda e clique em **Open**. Navegue até o diretório do repositório e selecione a pasta **ToDoListApp**, clique em OK, e o projeto será aberto.

4. Você pode conectar um dispositivo físico ou usar um emulador para executar o aplicativo.
  4.1. Para usar um dispositivo físico, é necessário conectá-lo ao computador via USB e ativar a depuração USB do seu Android: https://www.techtudo.com.br/dicas-e-tutoriais/2018/06/como-ativar-a-depuracao-usb-do-android.ghtml.
  4.2.  Para usar um emulador, verifique se há algum instalado e o selecione na aba **Device Manager**.
        Se não há nenhum instalado clique em **Device Manager** na tela acima e clique no botão **Create Device**. Na pop up que abrir, selecione o dispositivo desejado e siga até a instalação. Ao finalizar, selecione o dispositivo instalado.
        
5. Quando o dispositivo desejado estiver selecionado:
   <p align="center">
    <img width="25%" src="https://github.com/Rodrigo-Panta/deseonvolvimento-kotlin-android/blob/main/images/dispositivo-selecionado.png" />
   </p>
   
   clique no botão **Run App** para iniciar a aplicação:
   <p align="center">
    <img width="25%" src="https://github.com/Rodrigo-Panta/deseonvolvimento-kotlin-android/blob/main/images/run-app.png" />
   </p>

6. Se você estiver usando emulador, abra a aba *Emulator* para observar a execução do código.

7. Deve ser criado um aplicativo android com a tela inicial mostrada abaixo, e para inserir uma nova tarefa é só clicar em **Insira uma tarefa**
   e digitar a tarefa que deseja inserir. Ao clicar em **salvar** a terefa será adicionada na lista.
   
   <p align="center">
    <img width="25%" src="https://github.com/Rodrigo-Panta/deseonvolvimento-kotlin-android/blob/main/images/tela-lista.png" />
   </p>

8. Explore o aplicativo. Perceba que é possível inserir novos itens na lista e marcá-los como feitos. Como não há implementação de nenhum banco de dados, sempre que você abrir o aplicativo a lista vai estar vazia.



## Parte 2: Adicionando o comando de deleção na Todo List

Nessa parte do roteiro você irá inserir um botão **Remover** no aplicativo android, que fará a exclusão dos itens da lista que estiverem marcados como feitos. A inclusão do botão **Remover** será feita utilizando o código mostrado abaixo e acrescentando ele ao projeto inicial **ToDoListApp**. Não será necessário implementar 
nenhum código adicional, apenas copiar o código abaixo e colar no seu projeto.

Primeiro Vamos criar o botão na tela Principal com o ID **btnDeleteDone** e o texto **"Remover Feitos"**.

Abra o arquivo
```res -> layout -> activity_main.xml```

Selecione no canto superior direito o modo **Code** ou **Split** para conseguir visualizar o código a ser alterado.

Adicione o código abaixo após o último botão.

```xml
<Button
      android:id="@+id/btnDeleteDone"
      android:layout_width="414dp"
      android:layout_height="46dp"
      android:layout_marginBottom="44dp"
      android:text="Remover Feitos"
      app:layout_constraintBottom_toBottomOf="parent"
      app:layout_constraintEnd_toEndOf="parent"
      app:layout_constraintHorizontal_bias="1.0"
      app:layout_constraintStart_toStartOf="parent" />
```

Em seguida, vamos criar a função que remove da lista todos os itens marcados como feitos.

Abra o arquivo
```java -> com.example.todolistapp -> TodoAdapter```

Adicione função abaixo após **fun addTodo**

```kotlin
fun removeDone(){
  todos.removeAll{ todo ->
    todo.isChecked
  }
notifyDataSetChanged()
}
```
Por fim, falta apenas adicionar a ação no botão que chama a função.

Abra o arquivo 
```java -> com.example.todolistaap -> MainActivity```

Adicione o código abaixo após **fun btnAddTodo.setOnClickListener**

```kotlin
  btnDeleteDone.setOnClickListener{
    todoAdapter.removeDone()
  }
```



Sugestões no final: Incluir um BD local como SQLite para salvar os itens, 

