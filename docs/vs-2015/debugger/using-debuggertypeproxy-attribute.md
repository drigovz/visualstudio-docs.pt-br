---
title: Usando o atributo DebuggerTypeProxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684082"
---
# <a name="using-debuggertypeproxy-attribute"></a>Usando o atributo DebuggerTypeProxy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (AssetID:///T: System. Diagnostics. DebuggerTypeProxyAttribute? qualifyHint = false&AutoUpgrade = true) especifica um proxy ou um substituto para um tipo e altera a maneira como o tipo é exibido nas janelas do depurador. Quando você exibe uma variável que tem um proxy, o proxy substitui o tipo original em **exibição**. A janela de variáveis do depurador exibe apenas os membros públicos do tipo de proxy. Os membros particulares não são exibidos.  
  
 Esse atributo poderá ser aplicado a:  
  
- Estruturas  
  
- Classes  
  
- Assemblies  
  
  Uma classe de proxy de tipo deve ter um construtor que usa um argumento do tipo que o proxy substituirá. O depurador cria uma nova instância da classe de proxy de tipo sempre que precisa exibir uma variável do tipo de destino. Isso pode ter implicações de desempenho. Como resultado, você não deve fazer mais trabalho no construtor do que o que for absolutamente necessário.  
  
  Para minimizar penalidades de desempenho, o avaliador de expressão não examina os atributos no proxy de exibição do tipo a menos que o tipo seja expandido pelo clique do usuário no símbolo + na janela do depurador ou pelo uso de <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Consequentemente, você não deverá colocar os atributos no próprio tipo de exibição. Os atributos podem e devem ser usados no corpo do tipo de exibição.  
  
  É uma boa ideia para o proxy do tipo ser uma classe aninhada particular dentro da classe a que o atributo se destina. Isso permite acessar membros internos com facilidade.  
  
  Se <xref:System.Diagnostics.DebuggerTypeProxyAttribute> for usado no nível de assembly, o parâmetro `Target` especificará o tipo que o proxy substituirá.  
  
  Para obter um exemplo de como usar esse atributo junto com <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , consulte[usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Usando genéricos com DebuggerTypeProxy  
 O suporte para genéricos é limitado. Para C#, o `DebuggerTypeProxy` oferece suporte apenas a tipos abertos. Um tipo aberto, também chamada de um tipo não construído, é um tipo genérico que não foi instanciado com argumentos para seus parâmetros de tipo. Os tipos fechados, também chamados de tipos construídos, não têm suporte.  
  
 A sintaxe para um tipo aberto é semelhante ao seguinte:  
  
 `Namespace.TypeName<,>`  
  
 Se você usar um tipo genérico como um destino em `DebuggerTypeProxy`, deverá usar essa sintaxe. O mecanismo `DebuggerTypeProxy` infere os parâmetros de tipo para você.  
  
 Para obter mais informações sobre os tipos Open e closed em C#, consulte a [especificação da linguagem c#](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), seção 20.5.2 tipos abertos e fechados.  
  
 O Visual Basic não tem sintaxe de tipo aberto; portanto, você não pode fazer a mesma coisa no Visual Basic. Em vez disso, você deverá usar uma representação de cadeia de caracteres do nome do tipo aberto.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Consulte Também  
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Melhorando a depuração com os atributos de exibição do depurador](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
