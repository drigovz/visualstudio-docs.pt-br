---
title: Shell (isolado ou integrado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db0ab2c2a97f7cedde5b9b3a5ab925467a25146
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300480"
---
# <a name="shell-isolated-or-integrated"></a>Shell (isolado ou integrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode criar seu próprio aplicativo baseado no Visual Studio no modo integrado ou isolado. No modo integrado, muitos recursos do Visual Studio estão disponíveis além do seu aplicativo. No modo isolado, você escolhe um subconjunto de recursos do Visual Studio que deseja distribuir junto com sua própria extensão.  
  
## <a name="integrated-mode"></a>Modo integrado  
 O modo integrado permite que os usuários usem recursos padrão do Visual Studio junto com suas ferramentas personalizadas. O Shell integrado destina-se principalmente a hospedar linguagens de programação e ferramentas de desenvolvimento de software.  
  
 As ferramentas personalizadas criadas no Shell integrado são mescladas automaticamente com qualquer outra edição do Visual Studio instalada no mesmo computador. Você pode fornecer uma versão redistribuível do Shell integrado do Visual Studio se o Visual Studio ainda não estiver instalado.  
  
 A versão redistribuível do Shell integrado do Visual Studio não inclui linguagens de programação e os recursos que dão suporte a seus respectivos sistemas de projeto.  
  
> [!NOTE]
> O modo integrado do shell do Visual Studio pode ser instalado junto com todas as edições do Visual Studio, exceto as Express Editions.  
  
 Para obter mais informações, consulte [shell do Visual Studio (integrado)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Modo isolado  
 O modo isolado permite que você crie ferramentas personalizadas que são executadas lado a lado com outras versões do Visual Studio. Ele destina-se principalmente a ferramentas que podem acessar os serviços do Visual Studio sem depender de todos os recursos padrão do Visual Studio. Você pode personalizar a aparência dos aplicativos criados no Shell isolado do Visual Studio. Você pode desativar facilmente os recursos e os grupos de comandos de menu que você não deseja que apareçam junto com seu aplicativo.  
  
 Para obter mais informações, consulte [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuindo seu aplicativo de shell integrado ou isolado  
 Para distribuir seu aplicativo de shell integrado ou isolado, você precisa incluir seu aplicativo, um shell de redistribuição especial integrado ou isolado, e um programa de instalação. Para obter mais informações sobre distribuição e instalação, consulte [distribuindo aplicativos de shell isolados](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> O [EULA (contrato de licença de usuário final)](https://www.visualstudio.com/support/legal/mt171552) para os shells integrados e isolados do Visual Studio inclui uma seção sobre a coleta de dados (**seção 3. Dados**).  Ele descreve os dados de uso do cliente que podem ser coletados pela Microsoft de usuários do software Shell integrado ou isolado que você cria em seu aplicativo. Para obter mais informações, consulte [Microsoft Visual Studio declaração de privacidade da família de produtos](https://www.visualstudio.com/dn948229).  
> 
> Se você coletar dados de uso separados de seus clientes por meio de seu aplicativo, deverá fornecer um aviso apropriado aos usuários do seu aplicativo do que você coleta.  Ao distribuir o software Shell isolado ou integrado como parte de seu aplicativo, de acordo com a licença do Visual Studio Software Development Kit, você deve incluir um dos seguintes:  
> 
> - o contrato de licença de usuário final como parte de sua licença de aplicativo  
> - seu próprio EULA que exige que seus clientes concordem com os termos que protegem o Shell integrado ou isolado do Visual Studio pelo menos tanto quanto os termos de licença de usuário final da Microsoft para o software do Shell  
  
## <a name="additional-resources"></a>Recursos adicionais  
 Para obter mais informações sobre pacotes redistribuíveis, consulte o site de [downloads de extensibilidade do Visual Studio](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="see-also"></a>Consulte também  
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
