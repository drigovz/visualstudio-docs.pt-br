---
title: 'Como: Especifique onde os arquivos de cópias do Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226165"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Como: Especificar onde o Visual Studio copia os arquivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você publica um aplicativo usando o ClickOnce, o `Publish Location` propriedade especifica o local onde os arquivos de aplicativo e manifesto são colocados. Isso pode ser um caminho de arquivo ou o caminho para um servidor FTP.

 Você pode especificar o `Publish Location` propriedade no **Publish** página da **Designer de projeto**, ou usando o Assistente de publicação. Para obter mais informações, confira [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.

### <a name="to-specify-a-publishing-location"></a>Para especificar um local de publicação

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. Clique o **publicar** guia.

3. No **local de publicação** , insira o local de publicação usando um dos seguintes formatos:

   - Para publicar em um caminho de disco ou compartilhamento de arquivo, insira o caminho usando um caminho UNC (\\\Server\ApplicationName) ou um caminho de arquivo (C:\Deploy\ApplicationName).

   - Para publicar em um servidor FTP, insira o caminho usando o formato ftp:\//ftp.microsoft.com/ApplicationName.

     Observe que o texto precisa estar presente na caixa **Local de Publicação** para que o botão Procurar (**...**) funcione.

## <a name="see-also"></a>Consulte também
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md) [como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
