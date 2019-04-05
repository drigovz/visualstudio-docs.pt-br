---
title: 'CA3003: Examine o código para vulnerabilidades de injeção de caminho de arquivo'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018453"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Examine o código para vulnerabilidades de injeção de caminho de arquivo

|||
|-|-|
|NomeDoTipo|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Entrada de solicitação HTTP potencialmente não confiável de atingir o caminho de uma operação de arquivo.

## <a name="rule-description"></a>Descrição da regra

Ao trabalhar com entradas não confiáveis de solicitações da web, lembre-se de usar a entrada controlada pelo usuário ao especificar caminhos para arquivos. Um invasor pode ser capaz de ler um arquivo não intencional, resultando na divulgação de informações de dados confidenciais. Ou, um invasor pode ser capaz de gravar em um arquivo não intencional, resultando em modificação não autorizada de dados confidenciais ou comprometer a segurança do servidor. É uma técnica comum do invasor [percurso de caminho](https://www.owasp.org/index.php/Path_Traversal) para acessar os arquivos fora do diretório desejado.

Essa regra tenta encontrar a entrada de solicitações HTTP atingindo um caminho em uma operação de arquivo.

> [!NOTE]
> Essa regra não é possível acompanhar dados entre assemblies. Por exemplo, se um assembly lê a entrada de solicitação HTTP e, em seguida, passa-o para outro assembly que grava em um arquivo, essa regra não gerará um aviso.

> [!NOTE]
> Há um limite configurável para o nível de profundidade essa regra analisará o fluxo de dados em chamadas de método. Ver [configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber como configurar o limite em `.editorconfig` arquivos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

- Se possível, limite os caminhos de arquivo com base na entrada do usuário para uma lista segura explicitamente conhecida.  Por exemplo, se seu aplicativo precisa apenas acessar "red.txt", "green.txt" ou "blue.txt", permitir apenas esses valores.
- Verificar se há nomes de arquivo não confiável e validar o nome está bem-formado.
- Use nomes de caminho completos ao especificar caminhos.
- Evite construções potencialmente perigosas, como variáveis de ambiente path.
- Só aceitam nomes de arquivo longos e validar o nome longo se o usuário envia nomes curtos.
- Restringir a entrada do usuário final para caracteres válidos.
- Rejeite nomes em que o comprimento MAX_PATH foi excedido.
- A lidar com nomes de arquivo literalmente, sem serem interpretados.
- Determine se o nome do arquivo representa um arquivo ou um dispositivo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você tiver validado a entrada conforme descrito na seção anterior, é okey suprimir este aviso.

## <a name="pseudo-code-examples"></a>Exemplos de código pseudo

### <a name="violation"></a>Violação

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is: 
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display 
            // The content to the webpage. 
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is: 
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display 
            ' The content to the webpage. 
        End Using
    End Sub
End Class
```
