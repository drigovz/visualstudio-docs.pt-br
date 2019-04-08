---
title: Suporte para alterações de código (C# e Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9e840a8bb19b48c5cd4526ad80526bd62fcf8fa0
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526172"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Alterações de código suportadas (C# e Visual Basic)
Editar e Continuar trata a maioria dos tipos de alterações de código dentro dos corpos do método. A maioria das alterações fora dos corpos do método e algumas alterações dentro dos corpos do método, no entanto, não podem ser aplicadas durante a depuração. Para aplicar essas alterações sem suporte, você deverá parar a depuração e reinicializar com uma versão atualizada do código.

## <a name="supported-changes-to-code"></a>Alterações suportadas em código

A tabela a seguir mostra as alterações que podem ser feitas ao código C# e Visual Basic durante uma sessão de depuração sem reiniciar a sessão.

|Elemento de linguagem/recurso|Operação de edição com suporte|Limitações|
|-|-|-|
|Tipos|Adicionar métodos, campos, construtores, et al|[Sim](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Adicionar ou modificar|Não|
|expressões de Async e await|Adicionar ou modificar|[Sim](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objetos dinâmicos|Adicionar ou modificar|Não|
|expressões lambda|Adicionar ou modificar|[Sim](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expressões de LINQ|Adicionar ou modificar|[Mesmo que as expressões lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Geralmente, há suporte para mais recentes recursos de linguagem como interpolação de cadeia de caracteres e operadores nulo-condicional por editar e continuar. Para obter informações mais atuais, consulte o [Enc suporte edita](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) página.

## <a name="unsupported-changes-to-code"></a>Não há suporte para alterações no código
 As seguintes alterações não podem ser aplicadas ao código C# e Visual Basic durante uma sessão de depuração:

-   As alterações na instrução atual ou qualquer outra instrução ativa.

     As instruções ativas incluem todas as instruções, em funções na pilha de chamadas, que foram chamadas para acessar a instrução atual.

     A instrução atual é marcada por um plano de fundo amarelo na janela de origem. Outras instruções ativas são marcadas por um plano de fundo sombreado e são somente leitura. Essas cores padrão podem ser alteradas na caixa de diálogo **Opções**.

- A tabela a seguir mostra as alterações sem suporte para o código pelo elemento de linguagem.

|Elemento de linguagem/recurso|Operação de edição sem suporte|
|-|-|
|Todos os elementos de código|Renomear|
|Namespaces|Adicionar|
|Namespaces, tipos, membros|Excluir|
|Genéricos|Adicionar ou modificar|
|Interfaces|Modificar|
|Tipos|Adicionar membro abstrato ou virtual, adicione a substituição (consulte [detalhes](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipos|Adicionar destruidor|
|Membros|Modificar um membro fazendo referência a um tipo de interoperabilidade inserido|
|Membros (Visual Basic)|Modificar um membro com a instrução On Error ou retomar|
|Membros (Visual Basic)|Modificar um membro que contém uma cláusula de consulta de agregação, Group By, Join simples ou LINQ de junção de grupo|
|Métodos|Modificar assinaturas|
|Métodos|Tornar um método abstrato que se tornam não-abstrata, adicionando um corpo de método|
|Métodos|Excluir o corpo do método|
|Atributos|Adicionar ou modificar|
|Eventos ou propriedades|Modificar um parâmetro de tipo, o tipo base, tipo de delegado ou tipo de retorno |
|Operadores ou indexadores|Modificar um parâmetro de tipo, o tipo base, tipo de delegado ou tipo de retorno |
|blocos catch|Modificar quando ela contém uma instrução ativa|
|blocos try-catch-finally|Modificar quando ela contém uma instrução ativa|
|usando instruções|Adicionar|
|métodos/lambdas assíncronos|Modificar um método/lambda async em um projeto direcionado ao .NET Framework 4 e diminuir (consulte [detalhes](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificar um iterador em um projeto direcionado ao .NET Framework 4 e diminuir (consulte [detalhes](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Código não seguro
 Alterações no código não seguro têm as mesmas limitações que as alterações no código seguro, com uma restrição adicional: editar e continuar não dá suporte a alterações no código não seguro que saem de um método que contém o `stackalloc` operador.

## <a name="unsupported-app-scenarios"></a>Cenários de aplicativos sem suporte

Plataformas e aplicativos sem suporte incluem o ASP.NET 5, o Silverlight 5 e o Windows 8.1.

> [!NOTE]
> Aplicativos com suporte incluem UWP em x86 e x64 aplicativos destinados ao .NET Framework 4.6 e Windows 10 desktops ou versões posteriores (.NET Framework é apenas uma versão de área de trabalho).

## <a name="unsupported-scenarios"></a>Cenários sem suporte
 Editar e Continuar não está disponível nos seguintes cenários de depuração:

-   Depuração de modo misto (nativo/gerenciado).

-   Depuração de SQL.

-   Depurando um despejo do Dr. Watson.

-   Depurando um aplicativo inserido de tempo de execução.

-   Depurando um aplicativo usando anexar ao processo (**Depurar > Anexar ao processo**) em vez de executar o aplicativo escolhendo **inicie** do **depurar** menu.

-   Depurando código otimizado.

-   Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.

## <a name="see-also"></a>Consulte também
- [Editar e continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Como usar Editar e Continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)