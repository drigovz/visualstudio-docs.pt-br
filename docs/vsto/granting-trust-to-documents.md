---
title: Conceder confiança aos documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d245ddf00e4005b763bcd4437d3f8c18d05291e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986037"
---
# <a name="grant-trust-to-documents"></a>Conceder confiança aos documentos
  Um projeto de nível de documento tem os mesmos requisitos de segurança que os projetos de nível de aplicativo: assinando os manifestos com um certificado ou clicando no prompt de confiança. Além disso, o documento ou pasta de trabalho deve estar localizado em um diretório designado como um local confiável.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Locais confiáveis
 Os aplicativos no [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e no Office 2010 têm centros de confiança em que os usuários podem definir configurações de segurança e privacidade, como locais confiáveis. Para soluções do Office, o computador local é considerado um local confiável. No entanto, devido a um risco maior, há determinados diretórios que não podem nunca ser confiáveis, como as pastas temporárias do sistema, para cada usuário e para o Internet Explorer.

 Para obter mais informações sobre a central de confiabilidade, consulte [segurança e políticas e configurações no Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Para obter mais informações sobre como criar, gerenciar, remover e configurar pastas confiáveis, consulte [Configurar locais confiáveis e configurações de editores confiáveis no sistema do Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) e [criar, remover ou alterar um local confiável para seus arquivos](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Considerações de segurança para soluções do Office
 Há várias questões de segurança quando você considera quais pastas devem ser adicionadas aos locais confiáveis:

- As pastas locais são consideradas mais seguras e são implicitamente confiáveis. Locais remotos, como compartilhamentos de arquivos, devem ser designados como locais confiáveis.

- Quando você adiciona um diretório a locais confiáveis, essa ação concede confiança total não apenas a soluções do Office, mas também a VBA e a código ActiveX. Por esse motivo, o diretório raiz e as pastas *meus documentos* não devem ser designados como confiáveis.

- Embora o documento em si seja confiável usando os locais confiáveis, permissões adicionais são necessárias para confiar na personalização. Você pode conceder confiança total à personalização usando assinar os manifestos com um certificado, clicando no prompt de confiança ou instalando a solução do Office no diretório *arquivos de programas* .

- Você pode armazenar o documento ou a pasta de trabalho de uma solução em nível de documento no mesmo diretório que o assembly ou em um diretório diferente. Por exemplo, o documento pode estar localizado em um servidor do SharePoint e o assembly pode estar localizado em um compartilhamento de arquivos de rede. Para obter mais informações, consulte [como publicar uma solução do Office em nível de documento em um servidor do SharePoint usando o ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

## <a name="see-also"></a>Consulte também
- [Conceder confiança às soluções do Office](../vsto/granting-trust-to-office-solutions.md)
- [Solucionar problemas de segurança da solução do Office](../vsto/troubleshooting-office-solution-security.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
