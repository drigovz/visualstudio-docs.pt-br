---
title: 'Passo a passo: Criando um SDK usando JavaScript | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697500"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Passo a passo: crie um SDK usando JavaScript
Este passo a passo ensina como usar javaScript para criar um SDK matemático simples como uma Extensão visual studio (VSIX).  O passo a passo é dividido por estas partes:

- [Para criar o projeto SDK de extensão SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Para criar um aplicativo de exemplo que usa o SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Para JavaScript, não há nenhum tipo de projeto de biblioteca de classe. Neste passo a passo, o arquivo *sample aritmética.js* é criado diretamente no projeto VSIX. Na prática, recomendamos que você primeiro crie e teste os arquivos JavaScript e CSS como um aplicativo da Windows Store — por exemplo, usando o modelo **do Aplicativo em Branco** — antes de colocá-los em um projeto VSIX.

## <a name="prerequisites"></a>Pré-requisitos
 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Para criar o projeto SDK de extensão SimpleMathVSIX

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de categorias de modelos, em **Visual C#,** selecione **Extensibility**e selecione o modelo **do Projeto VSIX.**

3. Na caixa de texto `SimpleMathVSIX` **Nome,** especifique e escolha o botão **OK.**

4. Se o **Assistente de Pacote do Visual Studio** aparecer, escolha o botão **Seguinte** na página **Bem-vindo** e, em seguida, na **página 1 de 7**, escolha o botão **Concluir.**

     Embora o **Manifest Designer** abra, manteremos este passo a passo simples modificando o arquivo manifesto diretamente.

5. No **Solution Explorer,** abra o menu de atalho para o arquivo **source.extension.vsixmanifest** e, em seguida, escolha **'Código de exibição '''** Use este código para substituir o conteúdo existente no arquivo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. No **Solution Explorer,** abra o menu de atalho para o projeto **SimpleMathVSIX** e, em seguida, escolha **Adicionar** > **novo item**.

7. Na categoria **Dados,** selecione **arquivo XML,** nomeie o arquivo `SDKManifest.xml`e escolha o botão **Adicionar.**

8. No **Solution Explorer,** abra o menu de atalho para o arquivo **SDKManifest.xml** e, em seguida, escolha **Abrir** para exibir o arquivo no **Editor XML**.

9. Adicione o seguinte código ao arquivo **SDKManifest.xml.**

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. No **Solution Explorer**, no menu de atalho para o arquivo **SDKManifest.xml,** escolha **Propriedades**.

11. Na janela **Propriedades,** defina a propriedade Incluir na propriedade **VSIX** como **True**.

12. No **Solution Explorer,** no menu de atalho para o projeto **SimpleMathVSIX,** escolha **Adicionar** > **nova pasta**e, em seguida, nomeie a pasta `Redist`.

13. Adicionar subpastas em Redist para criar essa estrutura de pasta:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. No menu de atalho para a pasta **\js,\\ ** escolha **Adicionar** > **novo item**.

15. Em **itens Visuais C#,** selecione a categoria **Web** e selecione o item **Arquivo JavaScript.** Nomeie `arithmetic.js`o arquivo e escolha o botão **Adicionar.**

16. Insira o seguinte código em *aritmética.js:*

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. No **Solution Explorer**, no menu de atalho para o arquivo **aritmético.js,** escolha **Propriedades**. Faça essas alterações de propriedade:

    - Defina a **propriedade Include in VSIX** como **True**.

    - Defina a **propriedade Copiar para diretório de** saída para copiar **sempre**.

18. No **Solution Explorer**, no menu de atalho para o projeto **SimpleMathVSIX,** escolha **Construir**.

19. Depois que a compilação for concluída com sucesso, no menu de atalho para o projeto, escolha **Abrir pasta no Explorador de arquivos**. Navegue até **\bin\depuração\\**e execute-o. `SimpleMathVSIX.vsix`

20. Escolha o botão **Instalar** e deixe a instalação concluída.

21. Reinicie o Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Para criar um aplicativo de exemplo que usa o SDK

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de categorias de modelos, em **JavaScript,** selecione **Windows Store**e selecione o modelo do Aplicativo **em branco.**

3. Na **caixa Nome,** especifique `ArithmeticUI`. Clique no botão **OK**.

4. No **Solution Explorer,** abra o menu de atalho para o projeto **AritméticoUI** e escolha **Adicionar** > **referência**.

5. Em **Windows,** escolha **Extensões**e observe se **a Matemática Simples** é exibida.

6. Selecione a caixa de seleção **Matemática Simples** e escolha o botão **OK.**

7. No **Solution Explorer,** em **Referências,** observe que a referência **Matemática Simples** é exibida. Amplie-o e note que há uma pasta **\js\\ ** que inclui **aritmética.js**. Você pode abrir **aritmética.js** para confirmar que seu código fonte foi instalado.

8. Use o seguinte código para substituir o conteúdo de *default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Use o código a seguir para substituir o conteúdo de *\js\default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Substitua o conteúdo de *\css\default.css* por este código:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Escolha a chave **F5** para construir e executar o aplicativo.

12. Na ia do aplicativo, digite dois números, selecione uma operação e escolha o **=** botão. O resultado correto aparece.

## <a name="see-also"></a>Confira também
- [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)
