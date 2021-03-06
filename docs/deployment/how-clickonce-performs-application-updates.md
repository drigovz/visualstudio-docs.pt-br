---
title: Como o ClickOnce executa atualizações de aplicativos | Microsoft Docs
description: Saiba como o ClickOnce usa informações de versão de arquivo para decidir se deseja atualizar o aplicativo. O ClickOnce usa a aplicação de patches de arquivo para evitar redundância no download.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdef39a0ab07d4cb9c9f42cf897bd7728934b88d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915740"
---
# <a name="how-clickonce-performs-application-updates"></a>Como o ClickOnce executa atualizações de aplicativos
O ClickOnce usa as informações de versão de arquivo especificadas no manifesto de implantação do aplicativo para decidir se os arquivos do aplicativo devem ser atualizados. Depois que uma atualização é iniciada, o ClickOnce usa uma técnica chamada *aplicação de patch de arquivo* para evitar o download redundante de arquivos de aplicativo.

## <a name="file-patching"></a>Aplicação de patch de arquivo
 Ao atualizar um aplicativo, o ClickOnce não baixa todos os arquivos para a nova versão do aplicativo, a menos que os arquivos tenham sido alterados. Em vez disso, ele compara as assinaturas de hash dos arquivos especificados no manifesto do aplicativo para o aplicativo atual em relação às assinaturas no manifesto para a nova versão. Se as assinaturas de um arquivo forem diferentes, o ClickOnce baixará a nova versão. Se as assinaturas corresponderem, o arquivo não será alterado de uma versão para a próxima. Nesse caso, o ClickOnce copia o arquivo existente e o utiliza na nova versão do aplicativo. Essa abordagem impede que o ClickOnce precise baixar o aplicativo inteiro novamente, mesmo que apenas um ou dois arquivos tenham sido alterados.

 A aplicação de patch de arquivo também funciona para assemblies que são baixados sob demanda usando os <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> métodos e.

 Se você usar o Visual Studio para compilar seu aplicativo, ele gerará novas assinaturas de hash para todos os arquivos sempre que você recriar o projeto inteiro. Nesse caso, todos os assemblies serão baixados para o cliente, embora apenas alguns assemblies possam ter sido alterados.

 A aplicação de patches de arquivo não funciona para arquivos marcados como dados e armazenados no diretório de dados. Eles são sempre baixados, independentemente da assinatura de hash do arquivo. Para obter mais informações sobre o diretório de dados, consulte [acessar dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Confira também
- [Escolher uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Escolher uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)