---
title: Alterações de código com suporte (C# e Visual Basic) | Microsoft Docs
description: Entenda quais alterações de código têm suporte quando você está usando o recurso Editar e continuar durante a depuração de um projeto C# ou Visual Basic no Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 4fc3f49038a44b2b2bd5b467d6e1874f8a9a9803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940755"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Alterações de código com suporte (C# e Visual Basic)
Editar e Continuar trata a maioria dos tipos de alterações de código dentro dos corpos do método. A maioria das alterações fora dos corpos do método e algumas alterações dentro dos corpos do método, no entanto, não podem ser aplicadas durante a depuração. Para aplicar essas alterações sem suporte, você deverá parar a depuração e reinicializar com uma versão atualizada do código.

## <a name="supported-changes-to-code"></a>Alterações com suporte no código

A tabela a seguir mostra as alterações que podem ser feitas em C# e Visual Basic código durante uma sessão de depuração sem reiniciar a sessão.

|Recurso/elemento de linguagem|Operação de edição com suporte|Limitações|
|-|-|-|
|Tipos|Adicionar métodos, campos, construtores, et al|[Sim](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iterators|Adicionar ou modificar|Não|
|expressões Async/Await|Adicionar ou modificar|[Sim](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Objetos dinâmicos|Adicionar ou modificar|Não|
|expressões lambda|Adicionar ou modificar|[Sim](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Expressões LINQ|Adicionar ou modificar|[O mesmo que expressões lambda](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Recursos de idioma mais novos, como interpolação de cadeia de caracteres e operadores condicionais nulos, geralmente são suportados por editar e continuar. Para obter as informações mais atuais, consulte a página [edições com suporte do ENC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) .

## <a name="unsupported-changes-to-code"></a>Alterações sem suporte no código
 As seguintes alterações não podem ser aplicadas a código C# e Visual Basic durante uma sessão de depuração:

- As alterações na instrução atual ou qualquer outra instrução ativa.

     As instruções ativas incluem todas as instruções, em funções na pilha de chamadas, que foram chamadas para acessar a instrução atual.

     A instrução atual é marcada por um plano de fundo amarelo na janela de origem. Outras instruções ativas são marcadas por um plano de fundo sombreado e são somente leitura. Essas cores padrão podem ser alteradas na caixa de diálogo **Opções**.

- A tabela a seguir mostra alterações sem suporte no elemento código por linguagem.

|Recurso/elemento de linguagem|Operação de edição sem suporte|
|-|-|
|Todos os elementos de código|Renomear|
|Namespaces|Adicionar|
|Namespaces, tipos, membros|Excluir|
|Genéricos|Adicionar ou modificar|
|Interfaces|Modificar|
|Tipos|Adicionar membro abstrato ou virtual, adicionar substituição (consulte os [detalhes](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Tipos|Adicionar destruidor|
|Membros|Modificar um membro referenciando um tipo de interoperabilidade inserido|
|Membros|Modificar um membro estático depois que ele já tiver sido acessado executando o código|
|Membros (Visual Basic)|Modificar um membro com instrução On Error ou resume|
|Membros (Visual Basic)|Modificar um membro que contém uma cláusula de consulta LINQ de agregação, Group by, junção simples ou junção de grupo|
|Métodos|Modificar assinaturas|
|Métodos|Fazer com que um método abstrato se torne não-abstrato adicionando um corpo de método|
|Métodos|Excluir corpo do método|
|Atributos|Adicionar ou modificar|
|Eventos ou propriedades|Modificar um parâmetro de tipo, tipo base, tipo de representante ou tipo de retorno |
|Operadores ou indexadores|Modificar um parâmetro de tipo, tipo base, tipo de representante ou tipo de retorno |
|blocos catch|Modificar quando ele contém uma instrução ativa|
|blocos try – catch-finally|Modificar quando ele contém uma instrução ativa|
|usando instruções|Adicionar|
|métodos/lambdas assíncronos|Modificar um método/Lambda assíncrono em um projeto direcionado .NET Framework 4 e inferior (consulte os [detalhes](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iterators|Modificar um iterador em um projeto direcionado .NET Framework 4 e inferior (consulte os [detalhes](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Código não seguro
 As alterações no código não seguro têm as mesmas limitações que as alterações no código seguro, com uma restrição adicional: editar e continuar não oferece suporte a alterações em código não seguro que sai dentro de um método que contém o `stackalloc` operador.

## <a name="unsupported-app-scenarios"></a>Cenários de aplicativo sem suporte

Aplicativos e plataformas sem suporte incluem ASP.NET 5, Silverlight 5 e Windows 8.1.

> [!NOTE]
> Os aplicativos com suporte incluem UWP no Windows 10, e aplicativos x86 e x64 direcionados para a área de trabalho .NET Framework 4,6 ou versões posteriores (o .NET Framework é apenas uma versão da área de trabalho).

## <a name="unsupported-scenarios"></a>Cenários sem suporte
 Editar e Continuar não está disponível nos seguintes cenários de depuração:

- Depuração de modo misto (nativo/gerenciado).

- Depuração de SQL.

- Depurando um despejo de Dr. Watson.

- Depurando um aplicativo inserido de runtime.

- Depuração de um aplicativo usando anexar ao processo (**depurar > anexar ao processo**) em vez de executar o aplicativo escolhendo **Iniciar** no menu **depurar** .

- Depurando código otimizado.

- Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.

## <a name="see-also"></a>Confira também
- [Editar e continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Como usar Editar e Continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)