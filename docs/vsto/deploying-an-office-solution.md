---
title: Implantar uma solução do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a479f5318e232f748853dad8a41f9623f202d46
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648568"
---
# <a name="deploy-an-office-solution"></a>Implantar uma solução do Office
  Você pode implantar soluções do Office usando o ClickOnce ou o Windows Installer. Ao usar o ClickOnce, você reduz o número de etapas que a implantação e a atualização da sua solução exige. Usando o Windows Installer, você ganha controle de como uma solução é instalada e de quais páginas o programa de instalação exibe quando os usuários instalam a solução.  
  
> [!NOTE]  
>  Interessado em desenvolver soluções que estendem a experiência do Office em toda [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com soluções e suplementos do VSTO, e você pode criá-los usando quase qualquer tecnologia, como HTML5, JavaScript, CSS3 e XML de programação da web.  
  
## <a name="deploy-a-solution-by-using-clickonce"></a>Implantar uma solução usando o ClickOnce  
 Ao implantar uma solução usando o ClickOnce, você a publica em um local central onde os usuários podem instalá-la e executá-la. É possível atualizar a solução sem precisar distribuir um novo programa de instalação aos usuários.  Essa opção de implantação é mais simples, mas você não pode mostrar aos usuários as páginas de instalação personalizadas. Além disso, as soluções devem ser instaladas várias vezes em todos os computadores que possuem mais de um usuário. Ver [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploy-a-solution-by-using-windows-installer"></a>Implantar uma solução usando o Windows Installer  
 Ao implantar uma solução usando o Windows Installer, você distribui um programa de instalação aos usuários, e os usuários instalam a solução usando esse programa. O programa de instalação pode instalar uma solução para todos os usuários de um computador ao mesmo tempo, em vez de apenas para o usuário atual. Você também tem um pouco mais de controle sobre as opções que aparecem para os usuários quando eles instalam sua solução. Por exemplo, é possível mostrar um contrato de licenciamento ou permitir que os usuários instalem componentes específicos de uma solução. No entanto, se você atualizar a solução, será preciso distribuir um novo programa de instalação. Ver [implantar uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Consulte também  
 [Proteger as soluções do Office](../vsto/securing-office-solutions.md)   
 [Implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Implantar uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Solucionar problemas de implantação de solução do Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  