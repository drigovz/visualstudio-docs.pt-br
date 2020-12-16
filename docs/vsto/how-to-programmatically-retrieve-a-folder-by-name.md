---
title: 'Como: recuperar programaticamente uma pasta por nome'
description: Saiba como você pode usar o Visual Studio para recuperar programaticamente uma pasta por nome e, em seguida, exibir o conteúdo da pasta.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4e615897fedcbfa41ad7958e93354718d9ccfbc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528574"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Como: recuperar programaticamente uma pasta por nome
  Este exemplo obtém uma referência a uma pasta personalizada nomeada e, em seguida, exibe o conteúdo da pasta.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer:

- Uma pasta chamada TestFolder.

## <a name="see-also"></a>Veja também
- [Trabalhar com pastas](../vsto/working-with-folders.md)
- [Como: pesquisar programaticamente em uma pasta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Como: pesquisar programaticamente por um contato específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Como: criar programaticamente itens de pasta personalizados](../vsto/how-to-programmatically-create-custom-folder-items.md)
