---
title: Proteção por senha em documentos do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977894"
---
# <a name="password-protection-on-office-documents"></a>Proteção por senha em documentos do Office
  É possível definir uma senha em seus documentos do Microsoft Office Word e Microsoft Office pastas de trabalho do Excel para que eles não possam ser abertos por alguém que não saiba a senha. Essa opção é chamada **de senha ao abrir**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Você pode criar projetos de nível de documento usando documentos e pastas de trabalho existentes que têm a senha habilitada para **abrir** . O comportamento no Visual Studio é diferente para documentos do Word e do Excel que têm **senha ao abrir** habilitada.

 Para obter informações sobre como habilitar a **senha ao abrir**, consulte a ajuda no Word ou no Excel.

## <a name="behavior-of-excel-and-word"></a>Comportamento do Excel e do Word
 Sempre que você abre uma pasta de trabalho do Excel no Visual Studio que tem **senha ao abrir** habilitada, o Excel solicita a senha. Ao criar sua solução, a senha será solicitada novamente, pois o documento será aberto durante a compilação.

 Na primeira vez que você abrir um documento do Word no Visual Studio com a **senha aberta** habilitada, o Word solicitará a senha. Depois de inserir a senha com êxito, a **senha ao abrir** é removida do documento e a abertura do documento não exigirá mais uma senha. Se você quiser que o documento em sua solução exija uma senha para que possa ser aberto, você deve habilitar a **senha ao abrir** após a compilação final e antes de implantar a solução.

## <a name="see-also"></a>Confira também
- [Proteção de documentos em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Visão geral do gerenciamento de direitos de informação e extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Como: permitir que o código execute por trás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
