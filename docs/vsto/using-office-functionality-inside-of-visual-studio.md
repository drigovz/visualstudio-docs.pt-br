---
title: Usar a funcionalidade do Office no Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628657"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usar a funcionalidade do Office no Visual Studio
  Quando você cria um projeto de nível de documento, o documento e o aplicativo associado são hospedados dentro do Visual Studio para que você possa projetar e trabalhar diretamente com o documento. Quando você tiver um aplicativo aberto no Visual Studio do Microsoft Office, ele geralmente funciona conforme o esperado. No entanto, algumas das funcionalidades do aplicativo é diferente ou inacessível.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Proteção de documentos
 Microsoft Office Word e Microsoft Office Excel oferecem recursos de proteção que você pode usar em seus projetos para documento. No entanto, se a proteção de documentos é habilitada enquanto o documento está aberto no Visual Studio, ele poderá impedir você de fazer algumas alterações de design. Para obter mais informações, consulte [documentar a proteção em nível de documento soluções](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Gerenciamento de direitos de informação
 Gerenciamento de direitos de informação (IRM) está disponível no Microsoft Office Word e Microsoft Office Excel. IRM pode ajudar a impedir que pessoas não autorizadas de exibir ou alterar informações confidenciais. No entanto, o IRM também pode impedir seu código seja executado. Para obter mais informações, consulte [visão geral das extensões de código gerenciado e de gerenciamento de direitos de informação](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Proteção por senha
 Documentos do Microsoft Office Word e pastas de trabalho do Microsoft Office Excel podem ser definidas para que eles não podem ser abertos por alguém que sabe a senha. Proteção por senha é tratada diferentemente no Word e Excel e pode afetar o processo de desenvolvimento. Para obter mais informações, consulte [proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Consulte também
- [Proteção do documento em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Gerenciamento de direitos de informação e visão geral das extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)
- [Como: Abrir soluções do Office sem executar código](../vsto/how-to-open-office-solutions-without-running-code.md)
