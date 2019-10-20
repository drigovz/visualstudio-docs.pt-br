---
title: Refatoração (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667508"
---
# <a name="refactoring-c"></a>Refatoração (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A refatoração é o processo de aperfeiçoar seu código depois que ele é escrito alterando a estrutura interna do código sem alterar o comportamento externo do código.

 O C# Visual fornece os seguintes comandos de refatoração no menu **refatoração** :

- [Refatoração Extrair método (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refatoração Renomear (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Refatoração Encapsular campo (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refatoração Extrair Interface (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Refatoração Remover parâmetros (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Refatoração Reordenar parâmetros (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refatoração de vários projetos
 O Visual Studio dá suporte à refatoração de vários projetos para projetos que estão na mesma solução. Todas as operações de refatoração com referências corretas em todos os arquivos corrigem essas referências em todos os projetos do mesmo idioma. Isso funciona para qualquer referência projeto-para-projeto. Por exemplo, se você tiver um aplicativo de console que faça referência a uma biblioteca de classes, ao renomear um tipo de biblioteca de classes (usando a `Rename` operação de refatoração), as referências ao tipo de biblioteca de classes no aplicativo de console também serão atualizadas.

## <a name="changes-preview"></a>Visualização de alterações
 Muitas operações de refatoração fornecem uma oportunidade para que você examine todas as alterações de referência que uma operação de refatoração executaria em seu código antes de confirmar essas alterações. Para essas operações de refatoração, uma opção **Visualizar alterações de referência** será exibida na caixa de diálogo refatoração. Depois de selecionar essa opção e aceitar a operação de refatoração, a **caixa de diálogo Visualizar alterações** será exibida. Observe que a caixa de diálogo **Visualizar alterações** tem duas exibições. O modo de exibição inferior exibirá o código com todas as atualizações de referência devido à operação de refatoração. Pressionar **Cancelar** na caixa de diálogo **Visualizar alterações** irá parar a operação de refatoração e nenhuma alteração será feita no seu código.

## <a name="refactoring-warnings"></a>Avisos de refatoração
 Se o compilador não tiver uma compreensão completa do seu programa, e for possível que o mecanismo de refatoração não atualize todas as referências apropriadas, a caixa de diálogo de aviso será exibida. Essa caixa de diálogo de aviso também fornece uma oportunidade para você visualizar seu código na caixa de diálogo **Visualizar alterações** antes de confirmar as alterações.

> [!NOTE]
> Se um método contiver um erro de sintaxe (que o IDE indica com um sublinhado ondulado vermelho), o mecanismo de refatoração não atualizará nenhuma referência a um elemento dentro desse método. O exemplo a seguir ilustra esse comportamento.

 Por padrão, se você executar uma operação de refatoração sem Visualizar as alterações de referência e um erro de compilação for detectado em seu programa, o ambiente de desenvolvimento exibirá essa caixa de diálogo de aviso.

 Se você executar uma operação de refatoração que tenha **as alterações de referência de visualização** habilitadas e um erro de compilação for detectado em seu programa, o ambiente de desenvolvimento exibirá a seguinte mensagem de aviso na parte inferior das alterações de **Visualização** , em vez de exibir a caixa de diálogo de **aviso de refatoração** :

 **Seu projeto ou uma de suas dependências não são compiladas no momento. As referências não podem ser atualizadas.**

 Este aviso de refatoração está disponível somente para operações de refatoração que fornecem a opção de **alterações de referência de visualização** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Refatoração e resultados de verificação tolerantes a erros
 A refatoração é tolerante a erros. Em outras palavras, você pode executar uma refatoração em um projeto que não pode ser compilado. No entanto, nesses casos, o processo de refatoração pode não atualizar as referências ambíguas corretamente.

 A caixa de diálogo **resultados da verificação** poderá notificá-lo se o mecanismo de refatoração detectar erros de compilação ou descobrir que uma operação de refatoração inadvertidamente faz com que uma referência de código se vincule a algo diferente do que estava originalmente ligado ( problema de revinculação).

 Para ativar o recurso de resultados de verificação, no menu **ferramentas** , clique em **Opções**. Na caixa de diálogo **Opções** , expanda **Editor de texto**e, **C#** em seguida, expanda. Clique em **avançado** e marque a caixa de seleção **verificar resultados de refatoração** .

 A caixa de diálogo **resultados da verificação** distingue a diferença entre dois tipos de problemas de reassociação.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Referências cuja definição não será mais o símbolo renomeado
 Esse tipo de problema de revinculação ocorre quando uma referência não se refere a um símbolo renomeado. Por exemplo, considere o seguinte código:

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 Se você usar refatoração para renomear `a` para `b`, essa caixa de diálogo será exibida. A referência à variável renomeada `a` agora é associada ao parâmetro que é passado para o Construtor em vez de associação ao campo.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Referências cuja definição agora se tornará o símbolo renomeado
 Esse tipo de problema de reassociação ocorre quando uma referência que anteriormente não fazia referência ao símbolo renomeado agora faz referência ao símbolo renomeado. Por exemplo, considere o seguinte código:

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 Se você usar refatoração para renomear `OtherMethod` para `Method`, essa caixa de diálogo será exibida. A referência em `Main` agora se refere ao método sobrecarregado que aceita um parâmetro `int` em vez do método sobrecarregado que aceita um parâmetro `object`.

## <a name="see-also"></a>Consulte também
 [Usando o ambiente de desenvolvimento do Visual C# Studio para](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [saber como C# : restaurar trechos de refatoração](../ide/how-to-restore-csharp-refactoring-snippets.md)