---
title: 'Como: Abrir arquivos de texto, de forma programática, como pastas de trabalho'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d53c21247e18f198fdac1c22a3b38c0bc5348b6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633909"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Como: Abrir arquivos de texto, de forma programática, como pastas de trabalho
  Você pode abrir um arquivo de texto como uma pasta de trabalho. Você deve passar no nome do arquivo de texto que você deseja abrir. Você pode especificar vários parâmetros opcionais, como qual número de linha de análise em início e o formato de coluna dos dados no arquivo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer os seguintes componentes:

-   Um arquivo de texto delimitado por vírgula chamado `Test.txt` que contém pelo menos três linhas de texto.

-   O arquivo de texto `Test.txt` a ser armazenado na unidade C.

## <a name="see-also"></a>Consulte também
- [Trabalhar com pastas de trabalho](../vsto/working-with-workbooks.md)
- [Como: Abrir pastas de trabalho de forma programática](../vsto/how-to-programmatically-open-workbooks.md)
- [Como: Criar novas pastas de trabalho de forma programática](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Como: Salvar pastas de trabalho de forma programática](../vsto/how-to-programmatically-save-workbooks.md)
- [Como: Fechar pastas de trabalho de forma programática](../vsto/how-to-programmatically-close-workbooks.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
