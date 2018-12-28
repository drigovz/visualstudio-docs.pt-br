---
title: 'Como: Assinar soluções do Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 076cfcb6b63d650665e79a1e2d522595d4a82922
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804689"
---
# <a name="how-to-sign-office-solutions"></a>Como: Assinar soluções do Office
  Se você assinar uma solução, você pode conceder confiança à solução usando o certificado como prova. Você pode usar o mesmo certificado para várias soluções, e todas as soluções serão confiáveis sem atualizações de política de segurança adicional.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se você editar manualmente o aplicativo e manifestos de implantação usando o Manifest Generation and Editing Tool (*mage.exe* e *mageui.exe*), você deve assinar novamente os manifestos antes que você pode usá-los. Para obter mais informações, confira [Como: Assinar novamente os manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Entre usando um certificado
 Um certificado é um arquivo que contém uma chave exclusiva e a identidade do Editor de soluções. Você pode comprar certificados de autoridade de certificação, ou criar seu próprio certificado e tem uma autoridade de certificação assiná-lo.

 O Visual Studio assina soluções do Office com um certificado temporário para habilitar a depuração. Você não deve usar o certificado temporário em soluções implantadas como evidência.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Para assinar uma solução do Office por meio de um certificado

1.  Sobre o **Project** menu, clique em _SolutionName_**propriedades**.

2.  Clique na guia **Assinatura**.

3.  Selecione **assinar os manifestos do ClickOnce**.

4.  Localize o certificado clicando **selecione na Store** ou **selecionar do arquivo** e navegando até o certificado.

5.  Para verificar se o certificado correto está sendo usado, clique em **mais detalhes** para exibir as informações do certificado.

## <a name="see-also"></a>Consulte também

- [Proteger as soluções do Office](../vsto/securing-office-solutions.md)
- [Conceder confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md)
- [Página de Assinatura, Designer de Projeto](../ide/reference/signing-page-project-designer.md)
