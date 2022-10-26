# Desenvolvimento Mobile com Kotlin e Android
Este repositório contém um aplicativo android desenvolvido com a IDE Android Studio utilizando o modelo Empty Activity. 

O objetivo desse roteiro é permitir que o usuário tenha o primeiro contato com a linguagem Kotlin e adquira noções de desenvolvimento android com essa linguagem.

O aplicativo desenvolvido trata-se de uma simples lista de afazeres em que o usuário consegue inserir novas tarefas e marcá-las como prontas. 
Nesse roteiro, será implementada uma maneira de excluir tarefas que estão prontas.

## Parte 1: Instalação do projeto
Primeiramente, é necessária a instalação do Android Studio. Instale uma versão igual ou superior a **2021.3.1 Patch 1**

Siga o passo a passo presente no link abaixo para o sistema operacional adequado:
https://developer.android.com/studio/install?hl=pt-br

Após a instalação do Android Studio, siga os seguintes passos:

1. Faça um fork do repositório clicando no botão **Fork** no canto superior direito.

2. No terminal, clone o projeto com o seguinte comando:

```
git clone https://github.com/<SEU USUÁRIO>/desenvolvimento-kotlin-android.git
```
3. Abra o Android Studio. Na tela inicial, clique em **Projects** na aba lateral esquerda e clique em **Open**. Navegue até o diretório do repositório e selecione a pasta **TodoListApp**, clique em OK, e o projeto será aberto.

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

```kotlin
res->layout->activity_main.xml
java -> com.example.todolistaap->TodoAdapter
fun removeDone(){
  todos.removeAll{ todo ->
    todo.isChecked
  }
notifyDataSetChanged()
}
java -> com.example.todolistaap->MainActivity
  btnDeleteDone.setOnClickListener{
    todoAdapter.removeDone()
  }
```



  

Sugestões no final: Incluir um BD local como SQLite para salvar os itens, 

