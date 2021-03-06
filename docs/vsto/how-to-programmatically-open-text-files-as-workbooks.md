---
title: 'Como: abrir arquivos de texto programaticamente como pastas de trabalho'
description: Saiba como você pode usar o Visual Studio para abrir programaticamente um arquivo de texto como uma pasta de trabalho do Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47582718128fc9818bb42571e3f33c0190a32d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888739"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Como: abrir arquivos de texto programaticamente como pastas de trabalho
  Você pode abrir um arquivo de texto como uma pasta de trabalho. Você deve passar o nome do arquivo de texto que deseja abrir. Você pode especificar vários parâmetros opcionais, como qual número de linha iniciar a análise e o formato de coluna dos dados no arquivo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer os seguintes componentes:

- Um arquivo de texto delimitado por vírgulas chamado `Test.txt` que contém pelo menos três linhas de texto.

- O arquivo de texto `Test.txt` a ser armazenado na unidade C.

## <a name="see-also"></a>Confira também
- [Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)
- [Como: pastas de trabalho abertas programaticamente](../vsto/how-to-programmatically-open-workbooks.md)
- [Como criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Como: salvar pastas de trabalho programaticamente](../vsto/how-to-programmatically-save-workbooks.md)
- [Como: fechar pastas de trabalho programaticamente](../vsto/how-to-programmatically-close-workbooks.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
