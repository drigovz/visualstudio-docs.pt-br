---
title: Caracteres especiais para escape| Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632245"
---
# <a name="special-characters-to-escape"></a>Caracteres especiais para escape

Caracteres especiais devem ser de escape somente se tiverem um significado especial no contexto em que eles estiverem sendo usados. Por exemplo, o asterisco (*) é um caractere especial somente nos atributos "Incluir" e "Excluir" de uma definição de item ou em uma chamada para <xref:Microsoft.Build.Tasks.CreateItem>. Em outros casos, o asterisco é tratado como um asterisco literal. Embora você não precise que os asteriscos sejam de escape em todos os arquivos de projeto, fazer isso não é prejudicial.

 Use a notação %\<xx> no lugar do caractere especial, em que \<xx> representa o valor hexadecimal do caractere ASCII. Por exemplo, para usar um asterisco (*) como um caractere literal, use o valor `%2A`.

 Veja a seguir a lista completa de caracteres especiais de escape:

|Caractere|Descrição|
|---------------|-----------------|
|%|Sinal de porcentagem, usado para fazer referência a metadados.|
|$|Cifrão, usado para fazer referência a propriedades.|
|@|Sinal de arroba, usado para fazer referência a listas de itens.|
|(|Parênteses de abertura, usado em listas.|
|)|Parênteses de fechamento, usado em listas.|
|;|Ponto e vírgula, separador de lista.|
|?|Ponto de interrogação, um caractere curinga ao descrever uma especificação de arquivo na seção Incluir/Excluir de um item.|
|*|Asterisco, um caractere curinga ao descrever uma especificação de arquivo na seção Incluir/Excluir de um item.|

> [!NOTE]
> Em alguns cenários, você pode precisar escapar de caracteres `Exec` de citação dupla ("), como ao usar dentro de uma tarefa.

## <a name="see-also"></a>Confira também

- [Como: Escapar personagens especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
