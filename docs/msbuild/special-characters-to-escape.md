---
title: Caracteres especiais para escape| Microsoft Docs
description: Saiba mais sobre os caracteres especiais que devem ser ignorados somente se eles tiverem um significado especial no contexto em que estão sendo usados.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e665c214ea75de67a6c339bb516dfb812936448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878143"
---
# <a name="special-characters-to-escape"></a>Caracteres especiais para escape

Caracteres especiais devem ser de escape somente se tiverem um significado especial no contexto em que eles estiverem sendo usados. Por exemplo, o asterisco (*) é um caractere especial somente nos atributos "Incluir" e "Excluir" de uma definição de item ou em uma chamada para <xref:Microsoft.Build.Tasks.CreateItem>. Em outros casos, o asterisco é tratado como um asterisco literal. Embora você não precise que os asteriscos sejam de escape em todos os arquivos de projeto, fazer isso não é prejudicial.

 Use a% Notation \<xx> no lugar do caractere especial, em que \<xx> representa o valor hexadecimal do caractere ASCII. Por exemplo, para usar um asterisco (*) como um caractere literal, use o valor `%2A`.

 Veja a seguir a lista completa de caracteres especiais de escape:

|Caractere|Codificação ASCII|Descrição|
|---------|----------|-----------|
|%|%25|Sinal de porcentagem, usado para fazer referência a metadados.|
|$|%24|Cifrão, usado para fazer referência a propriedades.|
|@|%40|Sinal de arroba, usado para fazer referência a listas de itens.|
|(|%28|Parênteses de abertura, usado em listas.|
|)|%29|Parênteses de fechamento, usado em listas.|
|;|%3B|Ponto e vírgula, separador de lista.|
|?|%3F|Ponto de interrogação, um caractere curinga ao descrever uma especificação de arquivo na seção Incluir/Excluir de um item.|
|* |%2A|Asterisco, um caractere curinga ao descrever uma especificação de arquivo na seção Incluir/Excluir de um item.|

> [!NOTE]
> Em alguns cenários, talvez seja necessário escapar dos caracteres de aspas duplas ("), como ao usar dentro de uma `Exec` tarefa.

## <a name="see-also"></a>Confira também

- [Como: escapar caracteres especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
