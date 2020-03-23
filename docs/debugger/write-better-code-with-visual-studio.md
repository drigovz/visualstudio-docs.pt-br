---
title: Técnicas e ferramentas de depuração
description: Escreva um código melhor com menos bugs usando o Visual Studio para corrigir exceções, corrigir erros e melhorar seu código
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302024"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Depuração de técnicas e ferramentas para ajudá-lo a escrever um código melhor

Corrigir bugs e erros em seu código pode ser uma tarefa demorada e às vezes frustrante. Leva tempo para aprender a depurar efetivamente, mas um IDE poderoso como o Visual Studio pode tornar seu trabalho muito mais fácil. Um IDE pode ajudá-lo a corrigir erros e depurar seu código mais rapidamente, e não apenas isso, mas também pode ajudá-lo a escrever um código melhor com menos bugs. Nosso objetivo neste artigo é dar-lhe uma visão holística do processo de "correção de erros", para que você saiba quando usar o analisador de código, quando usar o depurador, como corrigir exceções e como codificar para intenção. Se você já sabe que precisa usar o depurador, consulte [Primeiro olhar para o depurador](../debugger/debugger-feature-tour.md).

Neste artigo, falamos sobre aproveitar o IDE para tornar suas sessões de codificação mais produtivas. Tocamos em várias tarefas, tais como:

* Prepare seu código para depuração aproveitando o analisador de código do IDE

* Como corrigir exceções (erros de tempo de execução)

* Como minimizar bugs codificando para intenção (usando a afirmação)

* Quando usar o depurador

Para demonstrar essas tarefas, mostramos alguns dos tipos mais comuns de erros e bugs que você encontrará ao tentar depurar seus aplicativos. Embora o código de amostra seja C#, as informações conceituais são geralmente aplicáveis a C++, Visual Basic, JavaScript e outras linguagens suportadas pelo Visual Studio (exceto quando anotada). As capturas de tela estão em C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Crie um aplicativo de exemplo com alguns bugs e erros nele

O código a seguir tem alguns bugs que você pode corrigir usando o Visual Studio IDE. O app aqui é um aplicativo simples que simula obter dados JSON de alguma operação, desserializar os dados para um objeto e atualizar uma lista simples com os novos dados.

Para criar o aplicativo:

1. Você deve ter o Visual Studio instalado e o desenvolvimento de **plataforma cruzada .NET Core** ou a carga de trabalho de desenvolvimento de desktop **.NET** instalada, dependendo do tipo de aplicativo que você deseja criar.

    Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/downloads/) do Visual Studio para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique em **Ferramentas** > **Obter Ferramentas e Recursos**. O Instalador do Visual Studio é iniciado. Escolha o **desenvolvimento de plataforma sem plataforma .NET Core** ou a carga de trabalho de desenvolvimento de desktop **.NET** e escolha **Modificar**.

1. Abra o Visual Studio.

    ::: moniker range=">=vs-2019"
    Na janela inicial, escolha **Criar um novo projeto**. Digite o **console** na caixa de pesquisa e escolha o **Aplicativo de Console (.NET Core)** ou **o Aplicativo de Console (.NET Framework).** Escolha **a seguir**. Digite um nome de projeto como **Console_Parse_JSON** e clique **em Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menu superior, escolha **Arquivo** > **Novo** > **Projeto**. No painel esquerdo da caixa de diálogo **do projeto Novo,** em **Visual C#**, escolha **Console App**e, em seguida, no painel médio escolha o Console **App (.NET Core)** ou **o Console App (.NET Framework)**. Digite um nome como **Console_Parse_JSON** e clique em **OK**.
    ::: moniker-end

    Se você não ver o modelo de projeto **Do Aplicativo para Console (.NET Core)** ou console **(.NET Framework),** vá para **Ferramentas** > **Obter Ferramentas e Recursos**, que abre o Visual Studio Installer. Escolha o **desenvolvimento de plataforma cruzada .NET Core** ou a carga de trabalho de desenvolvimento de desktop **.NET** e escolha **Modificar**.

    O Visual Studio criará o console do projeto, que será aberto no Gerenciador de Soluções no painel direito.

1. Substitua o código padrão no arquivo *Program.cs* do projeto pelo código de amostra abaixo.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Encontre os rabisques vermelhos e verdes!

Antes de tentar iniciar o aplicativo de exemplo e executar o depurador, verifique o código no editor de código para rabiscos vermelhos e verdes. Estes representam erros e avisos identificados pelo analisador de códigos do IDE. Os rabiscos vermelhos são erros de tempo de compilação, que você deve corrigir antes de executar o código. Os rabisques verdes são avisos. Embora muitas vezes você possa executar seu aplicativo sem corrigir os avisos, eles podem ser uma fonte de bugs e muitas vezes você economiza tempo e problemas investigando-os. Esses avisos e erros também aparecem na janela **Lista de erros,** se preferir uma exibição de lista.

No aplicativo de exemplo, você vê vários rabisques vermelhos que você precisa corrigir, e um verde que você vai olhar. Aqui está o primeiro erro.

![Erro mostrando como um rabiscar vermelho](../debugger/media/write-better-code-red-squiggle.png)

Para corrigir este erro, você verá outro recurso do IDE, representado pelo ícone da lâmpada.

## <a name="check-the-light-bulb"></a>Verifique a lâmpada!

O primeiro squiggle vermelho representa um erro de tempo de compilação. Paire sobre ele e ```The name `Encoding` does not exist in the current context```você vê a mensagem.

Observe que este erro mostra um ícone de lâmpada no inferior esquerdo. Juntamente com o ![ícone](../ide/media/screwdriver-icon.png)da chave de ![fenda](../ide/media/light-bulb-icon.png) ícone da chave de fenda, o ícone da lâmpada da lâmpada representa ações rápidas que podem ajudá-lo a corrigir ou refatorar o código inline. A lâmpada representa problemas que você *deve* corrigir. A chave de fenda é para problemas que você pode escolher para corrigir. Use a primeira correção sugerida para resolver esse erro clicando em **System.Text** à esquerda.

![Use a lâmpada para corrigir o código](../debugger/media/write-better-code-missing-include.png)

Quando você clica neste item, o Visual Studio adiciona a `using System.Text` declaração na parte superior do arquivo *Program.cs,* e o squiggle vermelho desaparece. (Quando você não tiver certeza do que uma correção sugerida fará, escolha o link **'Visualizar alterações** no direito' antes de aplicar a correção.)

O erro anterior é comum que você `using` geralmente corrige adicionando uma nova declaração ao seu código. Existem vários erros comuns e ```The type or namespace `Name` cannot be found.``` semelhantes a este, como esses tipos de erros, que podem indicar uma referência de montagem ausente (clique com o botão direito do mouse no projeto, escolha **Adicionar** > **referência),** um nome mal escrito ou uma biblioteca ausente que você precisa adicionar (para C#, clique com o botão direito do mouse no projeto e escolha **Gerenciar pacotes NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Corrigir os erros e avisos restantes

Há mais alguns rabiscos para olhar neste código. Aqui, você vê um erro de conversão de tipo comum. Quando você paira sobre o squiggle, você vê que o código está tentando converter uma string para um int, que não é suportado a menos que você adicione código explícito para fazer a conversão.

![Erro de conversão de tipo](../debugger/media/write-better-code-conversion-error.png)

Como o analisador de códigos não pode adivinhar sua intenção, não há lâmpadas para ajudá-lo desta vez. Para corrigir este erro, você precisa saber a intenção do código. Neste exemplo, não é muito difícil ver `points` que deve ser um valor numérico (inteiro), `points` `totalpoints`uma vez que você está tentando adicionar a .

Para corrigir esse erro, altere o `points` `User` membro da classe a partir disso:

```csharp
[DataMember]
internal string points;
```

para isto:

```csharp
[DataMember]
internal int points;
```

As linhas vermelhas no editor de código sumem.

Em seguida, paire sobre o squiggle `points` verde na declaração do membro de dados. O analisador de código diz que a variável nunca é atribuída a um valor.

![Mensagem de aviso para variável não atribuída](../debugger/media/write-better-code-warning-message.png)

Normalmente, isso representa um problema que precisa ser corrigido. No entanto, no aplicativo de exemplo você `points` está de fato armazenando dados na variável `totalpoints` durante o processo de desserialização e, em seguida, adicionando esse valor ao membro de dados. Neste exemplo, você sabe a intenção do código e pode ignorar o aviso com segurança. No entanto, se você quiser eliminar o aviso, você pode substituir o seguinte código:

```csharp
item.totalpoints = users[i].points;
```

por este:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

O squiggle verde vai embora.

## <a name="fix-an-exception"></a>Corrigir uma exceção

Quando você tiver consertado todos os rabiscos vermelhos e resolvidos - ou pelo menos investigados - todos os rabiscos verdes, você está pronto para iniciar o depurador e executar o aplicativo.

Pressione **F5** **(Debug > Iniciar depuração)** ou o botão **Iniciar depuração** ![Iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração") na barra de ferramentas Debug.

Neste ponto, o aplicativo `SerializationException` de amostra lança uma exceção (um erro de tempo de execução). Ou seja, o aplicativo engasga com os dados que está tentando serializar. Como você iniciou o aplicativo no modo de depuração (depurador anexado), o Helper de exceção do depurador leva você direto para o código que jogou a exceção e lhe dá uma mensagem de erro útil.

![Ocorre uma SerializaçãoException](../debugger/media/write-better-code-serialization-exception.png)

A mensagem de erro `4o` instrui-o de que o valor não pode ser analisado como um inteiro. Então, neste exemplo, você sabe que `4o` os `40`dados são ruins: devem ser . No entanto, se você não está no controle dos dados em um cenário real (digamos que você está recebendo-os de um serviço web), o que você faz sobre isso? Como consertar isso?

Quando você atinge uma exceção, você precisa fazer (e responder) algumas perguntas:

* Essa exceção é apenas um bug que você pode corrigir? Ou,

* Essa exceção é algo que seus usuários podem encontrar?

Se for o primeiro, conserte o inseto. (No aplicativo de exemplo, isso significa corrigir os dados ruins.) Se for o último, você pode precisar lidar com `try/catch` a exceção em seu código usando um bloco (analisamos outras estratégias possíveis na próxima seção). No aplicativo de exemplo, substitua o seguinte código:

```csharp
users = ser.ReadObject(ms) as User[];
```

por este código:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Um `try/catch` bloco tem algum custo de desempenho, então você só vai querer usá-los quando você realmente precisar deles, ou seja, onde (a) eles podem ocorrer na versão de lançamento do aplicativo, e onde (b) a documentação para o método indica que você deve verificar a exceção (assumindo que a documentação está completa!). Em muitos casos, você pode lidar com uma exceção adequadamente e o usuário nunca precisará saber sobre ela.

Aqui estão algumas dicas importantes para o manuseio de exceções:

* Evite usar um bloco `catch (Exception) {}`de captura vazio, como , que não tome as medidas apropriadas para expor ou lidar com um erro. Um bloco de captura vazio ou não informativo pode ocultar exceções e tornar seu código mais difícil de depurar em vez de mais fácil.

* Use `try/catch` o bloco em torno da`ReadObject`função específica que lança a exceção (, no aplicativo de amostra). Se você usá-lo em torno de um pedaço maior de código, você acaba escondendo a localização do erro. Por exemplo, não use `try/catch` o bloco em torno `ReadToObject`da chamada para a função pai, mostrado aqui, ou você não saberá exatamente onde a exceção ocorreu.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Para funções desconhecidas que você inclui em seu aplicativo, especialmente aquelas que interagem com dados externos (como uma solicitação web), verifique a documentação para ver quais exceções a função provavelmente lançará. Estas podem ser informações críticas para o tratamento adequado de erros e para depurar seu aplicativo.

Para o aplicativo de `SerializationException` exemplo, corrija o `GetJsonData` método alterando `4o` para `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Esclareça sua intenção de código usando a afirmação

Clique no botão **Restart** ![Restart App](../debugger/media/dbg-tour-restart.png "RestartApp") na barra de ferramentas Debug **(Ctrl** + **Shift** + **F5**). Isso reinicia o aplicativo em menos etapas. Você vê a saída a seguir na janela do console.

![Valor nulo na saída](../debugger/media/write-better-code-using-assert-null-output.png)

Você pode ver algo nesta saída que não está muito certo. **nome** e **sobrenome** para o terceiro registro estão em branco!

Este é um bom momento para falar sobre uma prática de `assert` codificação útil, muitas vezes subutilizada, que é usar instruções em suas funções. Adicionando o seguinte código, você inclui uma `firstname` verificação de tempo de execução para ter certeza de que e `lastname` não `null`são . Substitua o seguinte `UpdateRecords` código no método:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

por este:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Adicionando `assert` instruções como esta às suas funções durante o processo de desenvolvimento, você pode ajudar a especificar a intenção do seu código. No exemplo anterior, especificamos o seguinte:

* Uma seqüência válida é necessária para o primeiro nome
* Uma seqüência válida é necessária para o último nome

Ao especificar a intenção desta forma, você aplica suas exigências. Este é um método simples e útil que você pode usar para superfície bugs durante o desenvolvimento. (`assert` as declarações também são usadas como elemento principal nos testes unitários.)

Clique no botão **Restart** ![Restart App](../debugger/media/dbg-tour-restart.png "RestartApp") na barra de ferramentas Debug **(Ctrl** + **Shift** + **F5**).

> [!NOTE]
> O `assert` código está ativo apenas em uma compilação Debug.

Quando você reinicia, o depurador pausa `assert` na `users[i].firstname != null` declaração, porque a expressão avalia para `false` em vez de `true`.

![Afirmar resolve a falsa](../debugger/media/write-better-code-using-assert.png)

O `assert` erro diz que há um problema que você precisa investigar. `assert`pode cobrir muitos cenários onde você não necessariamente vê uma exceção. Neste exemplo, o usuário não verá uma `null` exceção, `firstname` e um valor é adicionado como em sua lista de registros. Isso pode causar problemas mais tarde (como você vê na saída do console) e pode ser mais difícil de depurar.

> [!NOTE]
> Em cenários onde você `null` chama um `NullReferenceException` método sobre o valor, um resultado. Você normalmente quer `try/catch` evitar o uso de um bloco para uma exceção geral, ou seja, uma exceção que não está vinculada à função de biblioteca específica. Qualquer objeto pode `NullReferenceException`lançar um . Verifique a documentação da função biblioteca se você não tiver certeza.

Durante o processo de depuração, é `assert` bom manter uma declaração específica até que você saiba que precisa substituí-la por uma correção de código real. Digamos que você decida que o usuário pode encontrar a exceção em uma compilação de versão do aplicativo. Nesse caso, você deve refatorar o código para garantir que seu aplicativo não lance uma exceção fatal ou resulte em algum outro erro. Então, para corrigir este código, substitua o seguinte código:

```csharp
if (existingUser == false)
{
    User user = new User();
```

por este código:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Ao usar este código, você preenche seus requisitos `firstname` de `lastname` código `null` e certifique-se de que um registro com um ou valor de não seja adicionado aos dados.

Neste exemplo, adicionamos `assert` as duas instruções dentro de um loop. Normalmente, ao `assert`usar, é melhor `assert` adicionar instruções no ponto de entrada (início) de uma função ou método. No momento, você `UpdateRecords` está olhando para o método no aplicativo de amostra. Neste método, você sabe que está em apuros se `null`qualquer um dos argumentos do método for , então verifique ambos com uma declaração `assert` no ponto de entrada da função.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Para as instruções anteriores, sua intenção`db`é que você`users`carregue dados existentes ( ) e recupere novos dados ( ) antes de atualizar qualquer coisa.

Você pode `assert` usar com qualquer tipo `true` de `false`expressão que resolva para ou . Então, por exemplo, você `assert` pode adicionar uma declaração como esta.

```csharp
Debug.Assert(users[0].points > 0);
```

O código anterior é útil se você quiser especificar a seguinte intenção: um novo valor de ponto maior que zero (0) é necessário para atualizar o registro do usuário.

## <a name="inspect-your-code-in-the-debugger"></a>Inspecione seu código no depurador

Ok, agora que você consertou tudo crítico que está errado com o aplicativo de amostra, você pode passar para outras coisas importantes!

Mostramos o Helper de exceção do depurador, mas o depurador é uma ferramenta muito mais poderosa que também permite que você faça outras coisas, como passar pelo seu código e inspecionar suas variáveis. Essas capacidades mais poderosas são úteis em muitos cenários, especialmente no seguinte:

* Você está tentando isolar um bug de tempo de execução em seu código, mas não é capaz de fazê-lo usando métodos e ferramentas discutidos anteriormente.

* Você quer validar o seu código, ou seja, assista-o enquanto ele corre para ter certeza de que ele está se comportando da maneira que você espera e fazendo o que você quer.

    É instrutivo observar seu código enquanto ele é executado. Você pode aprender mais sobre o seu código desta forma e muitas vezes pode identificar bugs antes que eles manifestem qualquer sintoma óbvio.

Para saber como usar os recursos essenciais do depurador, consulte [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Corrigir problemas de desempenho

Bugs de outro tipo incluem código ineficiente que faz com que seu aplicativo seja executado lentamente ou use muita memória. Geralmente, otimizar o desempenho é algo que você faz mais tarde no desenvolvimento do seu aplicativo. No entanto, você pode encontrar problemas de desempenho mais cedo (por exemplo, você vê que alguma parte do seu aplicativo está em andamento), e você pode precisar testar seu aplicativo com as ferramentas de criação de perfil no início. Para obter mais informações sobre ferramentas de criação de perfil, como a ferramenta de uso da CPU e o Analisador de Memória, consulte [Primeiro olhar para as ferramentas de criação de perfil](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Próximas etapas

Neste artigo, você aprendeu como evitar e corrigir muitos bugs comuns em seu código e quando usar o depurador. Em seguida, saiba mais sobre como usar o depurador visual studio para corrigir bugs.

> [!div class="nextstepaction"]
> [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md)
