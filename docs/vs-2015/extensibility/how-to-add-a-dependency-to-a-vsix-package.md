---
title: 'Como: Adicionar uma dependência a um pacote VSIX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cbd9426b7a9190872a2b04246d7f051b480a188d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066867"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: Adicionar uma dependência a um pacote do VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estão presentes no computador de destino. Para fazer isso, inclua as dependências VSIX para o arquivo vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para adicionar uma dependência  
  
1. Abra o arquivo vsixmanifest na **Design** modo de exibição. Vá para o **dependências** guia e clique em **New**.  
  
2. Para adicionar uma extensão instalada: na **adicionar nova dependência** caixa de diálogo, selecione **extensão instalada** e, em seguida, para o **nome**, selecione uma extensão na lista.  
  
3. Para adicionar outro VSIX que não está instalado:: na **adicionar nova dependência** caixa de diálogo, selecione **arquivo no sistema de arquivos** e, em seguida, usar o **procurar** botão para selecionar o VSIX.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparar extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
