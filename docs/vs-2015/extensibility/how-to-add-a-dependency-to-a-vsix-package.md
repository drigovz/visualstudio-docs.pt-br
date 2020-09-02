---
title: 'Como: adicionar uma dependência a um pacote VSIX | Microsoft Docs'
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
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697501"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como adicionar uma dependência a um pacote VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estão presentes no computador de destino. Para fazer isso, inclua as dependências do VSIX no arquivo Source. Extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Para adicionar uma dependência  
  
1. Abra o arquivo Source. Extension. vsixmanifest no modo de exibição de **design** . Vá para a guia **dependências** e clique em **novo**.  
  
2. Para adicionar uma extensão instalada: na caixa de diálogo **Adicionar nova dependência** , selecione a **extensão instalada** e, em seguida, para o **nome**, selecione uma extensão na lista.  
  
3. Para adicionar outro VSIX que não está instalado:: na caixa de diálogo **Adicionar nova dependência** , selecione **arquivo no sistema de arquivos** e, em seguida, use o botão **procurar** para selecionar o VSIX.  
  
## <a name="see-also"></a>Consulte Também  
 [Referência do esquema de extensão do VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparando extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
