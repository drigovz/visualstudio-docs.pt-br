---
title: Manifestos de aplicativo e implantação em soluções do Office
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc4095ce8cd945ff35903c9d8ffc95400cc3b7ab
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584432"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifestos de aplicativo e implantação em soluções do Office
  Um manifesto de aplicativo é um arquivo XML que fornece informações que são usadas por uma solução do Office para localizar e atualizar seus assemblies. Um manifesto de aplicativo pode ser usado com um manifesto de implantação, que é um arquivo XML armazenado no servidor que fornece as informações necessárias para localizar a versão mais atual do manifesto do aplicativo e dos assemblies.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Estrutura de manifesto para soluções do Office
 Para Microsoft Office soluções criadas usando as ferramentas de desenvolvimento do Office no Visual Studio, todos os manifestos se baseiam no esquema ClickOnce padrão. Quando você implanta suas soluções do Office, os manifestos do aplicativo para projetos de suplemento do no nível do documento e do VSTO estão localizados no cache do ClickOnce. Os manifestos de implantação não são copiados para o computador cliente.

 Para obter informações sobre o conteúdo de manifestos de aplicativo e implantação para projetos do Office, consulte [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md) e [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Criar manifestos de aplicativo e implantação
 Os manifestos de aplicativo são criados automaticamente como parte do processo de compilação. Toda vez que você cria um projeto de nível de documento, o local do manifesto de implantação é inserido no documento como uma propriedade de documento personalizada. Para suplementos do VSTO, o local do manifesto de implantação é armazenado no registro.

 Para obter mais informações sobre o **Assistente de publicação**, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Para obter mais informações sobre como os manifestos funcionam com as soluções do Office, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Confira também

- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)