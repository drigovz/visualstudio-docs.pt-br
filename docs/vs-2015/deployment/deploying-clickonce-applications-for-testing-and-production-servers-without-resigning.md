---
title: Implantação de aplicativos ClickOnce para testes e servidores de produção sem demissão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395380"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Implantando aplicativos ClickOnce para servidores de teste e produção sem assinar novamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico discute um novo recurso do ClickOnce introduzido na versão 3.5 do .NET Framework que permite a implantação de aplicativos ClickOnce a partir de vários locais de rede sem reassinar ou alterar os manifestos do ClickOnce.  
  
> [!NOTE]
> A demissão ainda é o método preferido para implantar novas versões de aplicativos. Sempre que possível, use o método de demissão. Para obter mais informações, consulte [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Desenvolvedores de terceiros e ISVs podem optar por esse recurso, facilitando a atualização de seus aplicativos por seus clientes. Este recurso pode ser usado nas seguintes situações:  
  
- Ao atualizar um aplicativo, não é a primeira instalação de um aplicativo.  
  
- Quando há apenas uma configuração do aplicativo em um computador. Por exemplo, se um aplicativo estiver configurado para apontar para dois bancos de dados diferentes, você não poderá usar esse recurso.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Excluindo implantaçãoProvedor de Manifestos de Implantação  
 No .NET Framework 2.0 e no .NET Framework 3.0, qualquer aplicativo ClickOnce que `deploymentProvider` instale no sistema para disponibilidade offline deve especificar um em seu manifesto de implantação. O `deploymentProvider` é frequentemente referido como o local de atualização; é o local em que o ClickOnce verificará as atualizações do aplicativo. Esse requisito, juntamente com a necessidade de os editores de aplicativos assinarem suas implantações, tornou difícil para uma empresa atualizar um aplicativo ClickOnce de um fornecedor ou outro terceiro. Também torna mais difícil implantar o mesmo aplicativo de vários locais na mesma rede.  
  
 Com as alterações feitas para o ClickOnce no Quadro .NET 3.5, é possível que um terceiro forneça um aplicativo ClickOnce para outra organização, que pode então implantar o aplicativo em sua própria rede.  
  
 Para aproveitar esse recurso, os desenvolvedores dos aplicativos `deploymentProvider` ClickOnce devem excluir de seus manifestos de implantação. Isso significa excluir `-providerUrl` o argumento quando você cria manifestos de implantação com o Mage.exe ou certificar-se de que a caixa de texto **Local de lançamento** na guia Manifesto de **aplicativo** seja deixada em branco se você estiver gerando manifestos de implantação com OMageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>implantaçãoAtualizações de provedores e aplicativos  
 Começando com o .NET Framework 3.5, você `deploymentProvider` não precisa mais especificar um manifesto de implantação para implantar um aplicativo ClickOnce para uso on-line e off-line. Isso suporta o cenário em que você precisa empacotar e assinar a implantação você mesmo, mas permitir que outras empresas implantem o aplicativo em suas redes.  
  
 O ponto chave a ser lembrado `deploymentProvider` é que os aplicativos que excluem um não podem `deploymentProvider` alterar seu local de instalação durante as atualizações, até que eles enviam uma atualização que inclua a tag novamente.  
  
 Aqui estão dois exemplos para esclarecer este ponto. No primeiro exemplo, você publica um `deploymentProvider` aplicativo ClickOnce que não tem `http://www.adatum.com/MyApplication/`tag e pede aos usuários para instalá-lo a partir de . Se você decidir publicar a próxima atualização `http://subdomain.adatum.com/MyApplication/`do aplicativo de , você não terá como significar `http://www.adatum.com/MyApplication/`isso no manifesto de implantação que reside em . Você pode fazer uma de duas coisas:  
  
- Diga aos seus usuários para desinstalar a versão anterior e instalar a nova versão a partir do novo local.  
  
- Inclua uma `http://www.adatum.com/MyApplication/` atualização que `deploymentProvider` inclua `http://www.adatum.com/MyApplication/`um apontamento para . Em seguida, libere `deploymentProvider` outra `http://subdomain.adatum.com/MyApplication/`atualização mais tarde apontando para .  
  
  No segundo exemplo, você publica um `deploymentProvider`aplicativo ClickOnce que especifica e, em seguida, decide removê-lo. Uma vez que `deploymentProvider` a nova versão sem ter sido baixada para os clientes, você não será capaz `deploymentProvider` de redirecionar o caminho usado para atualizações até que você libere uma versão do seu aplicativo que tenha sido restaurada. Como no primeiro `deploymentProvider` exemplo, deve inicialmente apontar para o local de atualização atual, não para sua nova localização. Neste caso, se você tentar `deploymentProvider` inserir um `http://subdomain.adatum.com/MyApplication/`que se refere a , então a próxima atualização falhará.  
  
## <a name="creating-a-deployment"></a>Criando uma implantação  
 Para obter orientações passo a passo sobre a criação de implantações que podem ser implantadas em diferentes locais de rede, consulte [Passo a Passo: Implantando manualmente um aplicativo ClickOnce que não requer re-assinatura e que preserva as informações de marca](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Consulte também  
 [Mage.exe (Ferramenta de Geração e Edição de Manifesto)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Ferramenta de Geração e Edição de Manifesto, Cliente Gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
