---
title: Gerenciamento de direitos de informação e visão geral das extensões de código gerenciado
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 109f6b85653a842f7c6fc9ce2d2c09b74113bbc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583914"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Gerenciamento de direitos de informação e visão geral das extensões de código gerenciado
  Microsoft Office Word e Microsoft Office Excel fornecem gerenciamento de direitos de informação (IRM), um recurso que pode ajudar a impedir que pessoas não autorizadas de exibir ou alterar informações confidenciais. Para obter detalhes sobre como funciona o gerenciamento de direitos de informações, consulte a Ajuda no aplicativo do Office específico.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Executar o código por trás de documentos com permissões restritas
 Se sua solução contiver um documento ou pasta de trabalho que usa o IRM, por padrão, Word e Excel não permitem que qualquer código seja executado. Se você for o autor do documento ou ter acesso de controle total, você pode alterar o padrão para que sua solução funcione. Para obter mais informações, confira [Como: Permitir que o código execute documentos code-behind com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 Impede o uso de IRM <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar ou manipular os dados armazenados em cache no documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Usuários finais para restringir permissões para documentos que usam extensões de código gerenciado
 Qualquer pessoa que tenha acesso de controle total para o documento ou pasta de trabalho em sua solução pode usar o IRM para restringir as permissões. Por exemplo, se um usuário final do departamento de contabilidade usa uma solução que preenche automaticamente uma planilha com os dados de um banco de dados, que o usuário talvez queira permitir acesso de leitura para outras pessoas e alterar acesso apenas às pessoas do seu departamento. Quando o usuário adiciona as permissões restritas, por padrão, não é possível executar o código por trás da planilha e planilha não será populada com dados.

 Para corrigir o problema, alguém com acesso de controle total para o documento ou pasta de trabalho deve alterar as configurações de permissão padrão para permitir o acesso programático ao modelo de objeto. Para obter mais informações, confira [Como: Permitir que o código execute documentos code-behind com permissões restritas](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Consulte também
- [Proteção do documento em soluções de nível de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Proteção por senha em documentos do Office](../vsto/password-protection-on-office-documents.md)
- [Proteger as soluções do Office](../vsto/securing-office-solutions.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
