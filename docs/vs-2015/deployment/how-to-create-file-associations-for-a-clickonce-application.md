---
title: 'Como: criar associações de arquivo para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82ffecdc719dad2f38208de00dc95438b3ff36ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697696"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Como criar associações de arquivo para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos podem ser associados a uma ou mais extensões de nome de arquivo, para que o aplicativo seja iniciado automaticamente quando o usuário abrir um arquivo desses tipos. Adicionar suporte à extensão de nome de arquivo a um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo é simples.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para criar associações de arquivo para um aplicativo ClickOnce  
  
1. Crie um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo normalmente ou use seu aplicativo existente [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
2. Abra o manifesto do aplicativo com um editor de texto ou XML, como o bloco de notas.  
  
3. Localize o elemento `assembly`. Para obter mais informações, consulte [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Como um filho do `assembly` elemento, adicione um `fileAssociation` elemento. O `fileAssociation` elemento tem quatro atributos:  
  
   - `extension`: A extensão de nome de arquivo que você deseja associar ao aplicativo.  
  
   - `description`: Uma descrição do tipo de arquivo, que será exibido no Shell do Windows.  
  
   - `progid`: Uma cadeia de caracteres que identifica exclusivamente o tipo de arquivo, para marcá-lo no registro.  
  
   - `defaultIcon`: Um ícone a ser usado para esse tipo de arquivo. O ícone deve ser adicionado como um recurso de arquivo no manifesto do aplicativo. Para obter mais informações, consulte [como: incluir um arquivo de dados em um aplicativo ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obter um exemplo dos `file` `fileAssociation` elementos e, consulte [ \<fileAssociation> Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Se você quiser associar mais de um tipo de arquivo ao aplicativo, adicione outros `fileAssociation` elementos. Observe que o `progid` atributo deve ser diferente para cada um.  
  
6. Depois de concluir o manifesto do aplicativo, assine novamente o manifesto. Você pode fazer isso na linha de comando usando Mage.exe.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Para obter mais informações, confira [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Consulte Também  
 [\<fileAssociation> Elementos](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
