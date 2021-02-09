---
title: Gerenciamento de direitos de informação & extensões de código gerenciado
description: Saiba mais sobre o Information Rights Management (IRM), um recurso que pode ajudá-lo a impedir que pessoas não autorizadas exibam ou alterem informações confidenciais.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc6a37a327c26ec46777575c3976c227e2d1de9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881484"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Visão geral do gerenciamento de direitos de informação e extensões de código gerenciado
  Microsoft Office Word e Microsoft Office Excel fornecem informações Rights Management (IRM), um recurso que pode ajudá-lo a impedir que pessoas não autorizadas exibam ou alterem informações confidenciais. Para obter detalhes sobre como as informações Rights Management funcionam, consulte a ajuda no aplicativo específico do Office.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Executar code-behind de documentos com permissões restritas
 Se sua solução contiver um documento ou pasta de trabalho que usa o IRM, por padrão, o Word e o Excel não permitirão a execução de qualquer código. Se você for o autor do documento ou tiver acesso de controle total, poderá alterar o padrão para que sua solução funcione. Para obter mais informações, consulte [como: permitir que o código execute por trás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 O IRM impede o uso do <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para recuperar ou manipular dados armazenados em cache no documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Usuários finais para restringir permissões a documentos que usam extensões de código gerenciado
 Qualquer pessoa que tenha acesso de controle total ao documento ou pasta de trabalho em sua solução pode usar o IRM para restringir permissões. Por exemplo, se um usuário final no departamento de contabilidade usar uma solução que preenche automaticamente uma planilha com dados de um banco de dado, esse usuário poderá querer permitir acesso de alteração somente a pessoas em seu departamento e acesso de leitura a outras pessoas. Quando o usuário adiciona as permissões restritas, por padrão, o código por trás da planilha não pode ser executado e a planilha não será preenchida com dados.

 Para corrigir o problema, alguém com acesso de controle total ao documento ou pasta de trabalho deve alterar as configurações de permissão padrão para permitir o acesso programático ao modelo de objeto. Para obter mais informações, consulte [como: permitir que o código execute por trás de documentos com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Confira também
- [Proteção de documentos em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
