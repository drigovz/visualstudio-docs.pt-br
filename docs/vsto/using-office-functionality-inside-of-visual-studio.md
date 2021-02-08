---
title: Usar a funcionalidade do Office dentro do Visual Studio
description: Saiba como o documento e o aplicativo associado de um projeto de nível de documento são hospedados dentro do Visual Studio para que você possa trabalhar diretamente com o documento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 258ea4529a558c91eb115b82b35def4ca4ab6561
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838230"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usar a funcionalidade do Office dentro do Visual Studio
  Quando você cria um projeto de nível de documento, o documento e o aplicativo associado são hospedados dentro do Visual Studio para que você possa criar e trabalhar diretamente com o documento. Quando você tem um aplicativo Microsoft Office aberto no Visual Studio, ele geralmente funciona conforme o esperado. No entanto, algumas das funcionalidades do aplicativo são diferentes ou inacessíveis.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Proteção de documentos
 Microsoft Office Word e Microsoft Office Excel oferecem recursos de proteção de documentos que você pode usar em seus projetos. No entanto, se a proteção de documentos estiver habilitada enquanto o documento estiver aberto no Visual Studio, ele poderá impedi-lo de fazer algumas alterações de design. Para obter mais informações, consulte [proteção de documentos em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Gerenciamento de direitos de informação
 O Rights Management de informações (IRM) está disponível em Microsoft Office Word e Microsoft Office Excel. O IRM pode ajudá-lo a impedir que pessoas não autorizadas exibam ou alterem informações confidenciais. No entanto, o IRM também pode impedir que seu código seja executado. Para obter mais informações, consulte [visão geral do gerenciamento de direitos de informação e extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Proteção por senha
 Microsoft Office documentos do Word e Microsoft Office pastas de trabalho do Excel podem ser definidos para que não possam ser abertos por alguém que não saiba a senha. A proteção por senha é tratada de forma diferente no Word e no Excel e pode afetar o processo de desenvolvimento. Para obter mais informações, consulte [proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Confira também
- [Proteção de documentos em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Visão geral do gerenciamento de direitos de informação e extensões de código gerenciado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)
- [Como: abrir soluções do Office sem executar código](../vsto/how-to-open-office-solutions-without-running-code.md)
