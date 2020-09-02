---
title: Extrair refatoração de interface (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667561"
---
# <a name="extract-interface-refactoring-c"></a>Refatoração Extrair Interface (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A interface de extração é uma operação de refatoração que fornece uma maneira fácil de criar uma nova interface com membros originados de uma classe, estrutura ou interface existente.

 Quando vários clientes usam o mesmo subconjunto de membros de uma classe, estrutura ou interface, ou quando várias classes, estruturas ou interfaces têm um subconjunto de membros em comum, pode ser útil incorporam o subconjunto de membros em uma interface. Para obter mais informações sobre como usar interfaces, consulte [interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 A interface de extração gera uma interface em um novo arquivo e posiciona o cursor no início do novo arquivo. Você pode especificar quais membros extrair na nova interface, o nome da nova interface e o nome do arquivo gerado usando a caixa de diálogo **extrair interface** .

### <a name="to-use-extract-interface"></a>Para usar a interface de extração

1. Crie um aplicativo de console chamado `ExtractInterface` e substitua `Program` pelo código a seguir

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Com o cursor posicionado em `MethodB` e clique em **extrair interface** no menu **refatorar** .

     A caixa de diálogo **extrair interface** é exibida.

     Você também pode digitar o atalho de teclado CTRL + R, I para exibir a caixa de diálogo **extrair interface** .

     Você também pode clicar com o botão direito do mouse, apontar para **refatorar**e, em seguida, clicar em **extrair interface** para exibir a caixa de diálogo **extrair interface** .

3. Clique em **selecionar tudo**.

4. Clique em **OK**.

     Você vê o novo arquivo, IProtoA.cs e o seguinte código:

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>Comentários
 Esse recurso só é acessível quando o cursor está posicionado na classe, struct ou interface que contém os membros que você gostaria de extrair. Quando o cursor estiver nessa posição, invoque a operação de refatoração Extrair interface.

 Quando você invoca a interface de extração em uma classe ou em uma estrutura, a lista bases e interfaces é modificada para incluir o novo nome da interface. Quando você invoca a interface de extração em uma interface, a lista bases e interfaces não é modificada.

## <a name="see-also"></a>Consulte Também
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)