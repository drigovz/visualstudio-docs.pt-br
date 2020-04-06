---
title: Como usar assistentes com modelos do projeto
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710542"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Como: Usar assistentes com modelos de projeto

O Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Studio fornece a interface que, quando implementada, permite executar código personalizado quando um usuário cria um projeto a partir de um modelo.

A personalização do modelo de projeto pode ser usada para exibir a iu personalizada que coleta a entrada do usuário para personalizar o modelo, adicionar arquivos adicionais ao modelo ou qualquer outra ação permitida em um projeto.

Os <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> métodos de interface são chamados em vários momentos enquanto o projeto está sendo criado, começando assim que um usuário clica em **OK** na caixa de diálogo **Do Novo Projeto.** Cada método da interface é nomeado para descrever o ponto em que é chamado. Por exemplo, o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Visual Studio liga imediatamente quando começa a criar o projeto, tornando-se um bom local para escrever código personalizado para coletar a entrada do usuário.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Crie um projeto de modelo de projeto com um projeto VSIX

Você começa a criar um modelo personalizado com o projeto de modelo de projeto, que faz parte do Visual Studio SDK. Neste procedimento, usaremos um projeto de modelo de projeto C#, mas também há um projeto de modelo de projeto Visual Basic. Em seguida, você adiciona um projeto VSIX à solução que contém o projeto de modelo de projeto.

1. Crie um projeto de modelo de projeto C# (no Visual Studio, selecione **File** > **New** > **Project** e procure por "modelo de projeto"). **Nomeie-o MyProjectTemplate**.

   > [!NOTE]
   > Você pode ser solicitado a instalar o Visual Studio SDK. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Adicione um novo projeto VSIX na mesma solução do projeto de modelo de projeto (no **Solution Explorer,** selecione o nó da solução, clique com o botão direito do mouse e selecione **Adicionar** > **novo projeto** e procure por "vsix"). Nomeie-o **MyProjectWizard.**

3. Defina o projeto VSIX como o projeto de startup. No **Solution Explorer,** selecione o nó do projeto VSIX, clique com o botão direito do mouse e selecione **Definir como Projeto de Inicialização**.

4. Adicione o projeto de modelo como um ativo do projeto VSIX. No **Solution Explorer**, sob o nó do projeto VSIX, encontre o arquivo *source.extension.vsixmanifest.* Clique duas vezes para abri-lo no editor do manifesto.

5. No editor de manifestos, selecione a guia **Ativos** no lado esquerdo da janela.

6. Na guia **Ativos,** selecione **Novo**. Na **janela Adicionar novo ativo,** para o campo Tipo, selecione **Microsoft.VisualStudio.ProjectTemplate**. No campo **Origem,** selecione **Um projeto na solução atual**. No **campo Projeto,** selecione **MyProjectTemplate**. Em seguida, clique em **OK**.

7. Compile a solução e inicie a depuração. Uma segunda instância do Visual Studio é exibida. (Isso pode levar alguns minutos).

8. Na segunda instância do Visual Studio, tente criar um novo projeto com seu novo modelo (**File** > **New** > **Project**, procure por "myproject"). O novo projeto deve aparecer com uma classe chamada **Class1**. Você criou agora um modelo de projeto personalizado! Pare de depurar agora.

## <a name="create-a-custom-template-wizard"></a>Crie um assistente de modelo personalizado

Este procedimento mostra como criar um assistente personalizado que abre um Formulário do Windows antes de o projeto ser criado. O formulário permite que os usuários adicionem um valor de parâmetro personalizado que é adicionado ao código-fonte durante a criação do projeto.

1. Configure o projeto VSIX para permitir que ele crie uma montagem.

2. No **Solution Explorer,** selecione o nó do projeto VSIX. Abaixo **do Solution Explorer**, você deve ver a janela **Propriedades.** Se não o fizer, selecione **Exibir** > **janela de propriedades**ou pressione **F4**. Na janela **Propriedades,** selecione `true`os seguintes campos para:

   - **Incluir montagem no recipiente VSIX**

   - **Inclua símbolos de depuração no contêiner VSIX**

   - **Incluir símbolos de depuração na implantação local do VSIX**

3. Adicione a montagem como um recurso ao projeto VSIX. Abra o arquivo *source.extension.vsixmanifest* e selecione a guia **Ativos.** Na **janela Adicionar novo ativo,** para **Tipo** selecione **Microsoft.VisualStudio.Assembly**, para **selecionar Origem** **Um projeto na solução atual**e para **O Projeto** selecionar **MyProjectWizard**.

4. Adicione as seguintes referências ao projeto VSIX. (No **Solution Explorer,** no nó do projeto VSIX, selecione **Referências,** clique com o botão direito do mouse e **selecione Adicionar referência**.) Na caixa de diálogo **Adicionar referência,** na guia **'Estrutura',** encontre o conjunto **System.Windows Forms** e selecione-o. Encontre também e selecione os conjuntos **Sistema** e **Sistema.Desenho.** Agora selecione a guia **Extensões.** Encontre o conjunto **EnvDTE** e selecione-o. Também encontre o **conjunto Microsoft.VisualStudio.TemplateWizardInterface** e selecione-o. Clique em **OK**.

5. Adicione uma classe para a implementação do assistente ao projeto VSIX. (No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto VSIX e selecione **Adicionar,** em seguida, **Novo Item,** depois **Classe**.) Nomeie a classe **WizardImplementation**.

6. Substitua o código no arquivo *WizardImplementationClass.cs* pelo seguinte código:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    O **UserInputForm** referenciado neste código será implementado posteriormente.

    A `WizardImplementation` classe contém implementações de <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>métodos para cada membro de . Neste exemplo, apenas <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> o método executa uma tarefa. Todos os outros métodos `true`não fazem nada ou retornam.

    O <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> método aceita quatro parâmetros:

   - Um <xref:System.Object> parâmetro que pode ser <xref:EnvDTE._DTE> lançado para o objeto raiz, para permitir que você personalize o projeto.

   - Um <xref:System.Collections.Generic.Dictionary%602> parâmetro que contém uma coleção de todos os parâmetros pré-definidos no modelo. Para obter mais informações sobre os parâmetros do modelo, consulte [parâmetros de modelo](../ide/template-parameters.md).

   - Um <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parâmetro que contém informações sobre que tipo de modelo está sendo usado.

   - Uma <xref:System.Object> matriz que contém um conjunto de parâmetros passados para o assistente pelo Visual Studio.

     Este exemplo adiciona um valor de parâmetro <xref:System.Collections.Generic.Dictionary%602> do formulário de entrada do usuário ao parâmetro. Cada instância `$custommessage$` do parâmetro no projeto será substituída pelo texto inserido pelo usuário.

7. Agora crie o **UserInputForm**. No arquivo *WizardImplementation.cs,* adicione o seguinte código `WizardImplementation` após o término da classe.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    O formulário de entrada do usuário fornece um formulário simples para inserir um parâmetro personalizado. O formulário contém uma `textBox1` caixa de `button1`texto nomeada e um botão chamado . Quando o botão é clicado, o texto `customMessage` da caixa de texto é armazenado no parâmetro.

## <a name="connect-the-wizard-to-the-custom-template"></a>Conecte o assistente ao modelo personalizado

Para que seu modelo de projeto personalizado use seu assistente personalizado, você precisa assinar o conjunto do assistente e adicionar algumas linhas ao seu modelo de projeto personalizado para que ele saiba onde encontrar a implementação do assistente quando um novo projeto for criado.

1. Assine a montagem. No **Solution Explorer,** selecione o projeto VSIX, clique com o botão direito do mouse e selecione **Propriedades do projeto**.

2. Na janela Propriedades do projeto, selecione a guia **Assinar.** na guia **Assinar,** verifique **'Assinar o conjunto ''''Propriedades** **do projeto'.** No **campo Escolher um arquivo de chave nome forte,** selecione ** \<Nova>**. Na **janela Criar nome forte,** no campo Nome do **arquivo Chave,** **digite key.snk**. Desmarque o **arquivo proteger meu arquivo-chave com um** campo de senha.

3. No **Solution Explorer,** selecione o projeto VSIX e encontre a janela **Propriedades.**

4. Defina o **campo ''Criar de compilação de cópia'** para o campo Diretório de saída como **verdadeiro**. Isso permite que o conjunto seja copiado para o diretório de saída quando a solução for reconstruída. Ainda está contido `.vsix` no arquivo. Você precisa ver a assembléia para descobrir sua chave de assinatura.

5. Recriar a solução.

6. Agora você pode encontrar o arquivo key.snk no diretório do projeto MyProjectWizard (*\<sua localização de disco>\MyProjectTemplate\MyProjectWizard\key.snk*). Copie o arquivo *key.snk.*

7. Vá para o diretório de saída e encontre o conjunto*\<(localização do disco>\MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Cole o arquivo *key.snk* aqui. (Isso não é absolutamente necessário, mas tornará as seguintes etapas mais fáceis.)

8. Abra uma janela de comando e mude para o diretório no qual a montagem foi criada.

9. Encontre a ferramenta de assinatura *sn.exe.* Por exemplo, em um sistema operacional windows 10 de 64 bits, um caminho típico seria o seguinte:

     *C:\Arquivos de programa (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Ferramentas*

     Se você não conseguir encontrar a ferramenta, tente executar **onde /R . sn.exe** na janela de comando. Anote o caminho.

10. Extrair a chave pública do arquivo *key.snk.* Na janela de comando, digite

     **\<localização de sn.exe>\sn.exe -p key.snk outfile.key.**

     Não se esqueça de cercar o caminho do *sn.exe* com aspas se houver espaços nos nomes dos diretórios!

11. Obtenha o token de chave pública do arquivo de saída:

     **\<localização de sn.exe>\sn.exe -t outfile.key.**

     Mais uma vez, não se esqueça das aspas. Você deve ver uma linha na saída como esta

     **O token \<de chave pública é o token>**

     Anote esse valor.

12. Adicione a referência ao assistente personalizado ao arquivo *.vstemplate* do modelo do projeto. No **Solution Explorer,** encontre o arquivo chamado *MyProjectTemplate.vstemplate*e abra-o. Após o término \<da seção TemplateContent>, adicione a seguinte seção:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Onde **MyProjectWizard** é o nome do conjunto, e **token** é o token que você copiou na etapa anterior.

13. Salve todos os arquivos do projeto e reconstrua.

## <a name="add-the-custom-parameter-to-the-template"></a>Adicione o parâmetro personalizado ao modelo

Neste exemplo, o projeto usado como modelo exibe a mensagem especificada na forma de entrada do usuário do assistente personalizado.

1. No **Solution Explorer,** vá para o projeto **MyProjectTemplate** e abra *Class1.cs*.

2. No `Main` método da aplicação, adicione a seguinte linha de código.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    O parâmetro `$custommessage$` é substituído pelo texto inserido no formulário de entrada do usuário quando um projeto é criado a partir do modelo.

Aqui está o arquivo de código completo antes de ser exportado para um modelo.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Use o assistente personalizado

Agora você pode criar um projeto a partir do seu modelo e usar o assistente personalizado.

1. Reconstrua a solução e comece a depurar. Uma segunda instância do Visual Studio deve ser exibida.

2. Crie um novo projeto MyProjectTemplate. **(Arquivo** > **Novo** > **Projeto**).

3. Na caixa de diálogo **Novo Projeto,** procure por "myproject" para localizar seu modelo, digitar um nome e clicar em **OK**.

     O formulário de entrada do usuário assistente é aberto.

4. Digite um valor para o parâmetro personalizado e clique no botão.

     O formulário de entrada do usuário assistente fecha e um projeto é criado a partir do modelo.

5. No **Solution Explorer,** clique com o botão direito do mouse no arquivo de código-fonte e clique **em Exibir código**.

     Observe `$custommessage$` que foi substituído pelo texto inserido no formulário de entrada do usuário assistente.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Personalizar modelos](../ide/customizing-project-and-item-templates.md)
- [Elemento WizardExtension (modelos do Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Pacotes NuGet em modelos do Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
