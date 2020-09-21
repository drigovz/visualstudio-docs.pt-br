---
title: Problemas de segurança, controle de versão e manifesto em implantações do ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4864d37cb5930075b292ee765bce9b288794019
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838408"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemas de segurança, controle de versão e manifesto em implantações do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Há uma variedade de problemas com [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] segurança, controle de versão de aplicativo e sintaxe e semântica de manifesto que podem fazer com que uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação não seja bem sucedido.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>Controle de conta de usuário do ClickOnce e do Windows Vista  
 No [!INCLUDE[windowsver](../includes/windowsver-md.md)] , os aplicativos, por padrão, são executados como um usuário padrão, mesmo que o usuário atual esteja conectado com uma conta que tenha permissões de administrador. Se um aplicativo deve executar uma ação que exige permissões de administrador, ele informa ao sistema operacional que solicita ao usuário que insira suas credenciais de administrador. Esse recurso, que é chamado de UAC (controle de conta de usuário), impede que os aplicativos façam alterações que possam afetar todo o sistema operacional sem a aprovação explícita de um usuário. Os aplicativos do Windows declaram que exigem essa elevação de permissão, especificando o `requestedExecutionLevel` atributo na `trustInfo` seção do manifesto do aplicativo.  
  
 Devido ao risco de expor aplicativos a ataques de elevação de segurança, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos não poderão solicitar elevação de permissão se o UAC estiver habilitado para o cliente. Qualquer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo que tente definir seu `requestedExecutionLevel` atributo como `requireAdministrator` ou `highestAvailable` não será instalado no [!INCLUDE[windowsver](../includes/windowsver-md.md)] .  
  
 Em alguns casos, seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo pode tentar executar com permissões de administrador devido à lógica de detecção do instalador em [!INCLUDE[windowsver](../includes/windowsver-md.md)] . Nesse caso, você pode definir o `requestedExecutionLevel` atributo no manifesto do aplicativo como `asInvoker` . Isso fará com que o próprio aplicativo seja executado sem elevação. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] adiciona automaticamente esse atributo a todos os manifestos do aplicativo.  
  
 Se você estiver desenvolvendo um aplicativo que exige permissões de administrador para o tempo de vida inteiro do aplicativo, considere implantar o aplicativo usando a tecnologia Windows Installer (MSI) em vez disso. Para obter mais informações, consulte [noções básicas do Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Cotas de aplicativos online e aplicativos de confiança parcial  
 Se seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo for executado online em vez de por meio de uma instalação, ele deverá se ajustar dentro da cota reservada para aplicativos online. Além disso, um aplicativo de rede que é executado em confiança parcial, como com um conjunto restrito de permissões de segurança, não pode ser maior que metade do tamanho da cota.  
  
 Para obter mais informações e instruções sobre como alterar a cota do aplicativo online, consulte [visão geral do cache do ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemas de controle de versão  
 Você poderá ter problemas se atribuir nomes fortes ao assembly e incrementar o número de versão do assembly para refletir uma atualização do aplicativo. Qualquer assembly compilado com uma referência a um assembly de nome forte deve ser recompilado, ou o assembly tentará referenciar a versão mais antiga. O assembly tentará isso porque o assembly está usando o valor da versão antiga em sua solicitação de associação.  
  
 Por exemplo, digamos que você tenha um assembly de nome forte em seu próprio projeto com a versão 1.0.0.0. Depois de compilar o assembly, você o adiciona como uma referência ao projeto que contém seu aplicativo principal. Se você atualizar o assembly, incrementar a versão para 1.0.0.1 e tentar implantá-lo sem também recompilar o aplicativo, o aplicativo não será capaz de carregar o assembly em tempo de execução.  
  
 Esse erro só poderá ocorrer se você estiver editando seus [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestos manualmente; você não terá esse erro se você gerar a implantação usando o [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] .  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Especificando assemblies de .NET Framework individuais no manifesto  
 Seu aplicativo não será carregado se você tiver editado manualmente uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação para fazer referência a uma versão mais antiga de um [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] assembly. Por exemplo, se você adicionou uma referência ao assembly System.Net para uma versão do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] anterior à versão especificada no manifesto, ocorrerá um erro. Em geral, você não deve tentar especificar referências a assemblies individuais [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , pois a versão do na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] qual seu aplicativo é executado é especificada como uma dependência no manifesto do aplicativo.  
  
## <a name="manifest-parsing-issues"></a>Problemas de análise de manifesto  
 Os arquivos de manifesto usados pelo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] são arquivos XML e devem ser bem formados e válidos: eles devem obedecer às regras de sintaxe XML e usar apenas elementos e atributos definidos no esquema XML relevante.  
  
 Algo que pode causar problemas em um arquivo de manifesto está selecionando um nome para seu aplicativo que contém um caractere especial, como uma aspa simples ou dupla. O nome do aplicativo faz parte de sua [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identidade. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Atualmente, o não analisa as identidades que contêm caracteres especiais. Se o aplicativo não for ativado, verifique se você está usando apenas caracteres alfabéticos e numéricos para o nome e tente implantá-lo novamente.  
  
 Se você editou manualmente seus manifestos de implantação ou de aplicativo, você pode tê-los corrompidos involuntariamente. O manifesto corrompido impedirá uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalação correta. Você pode depurar esses erros em tempo de execução clicando em **detalhes** na caixa de diálogo **erro do ClickOnce** e lendo a mensagem de erro no log. O log listará uma das seguintes mensagens:  
  
- Uma descrição do erro de sintaxe e o número da linha e a posição do caractere em que o erro ocorreu.  
  
- O nome de um elemento ou atributo usado na violação do esquema do manifesto. Se você adicionou o XML manualmente aos seus manifestos, precisará comparar suas adições aos esquemas de manifesto. Para obter mais informações, consulte [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) e manifesto do [aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).  
  
- Um conflito de ID. Referências de dependência em manifestos de implantação e de aplicativo devem ser exclusivas em seus `name` `publicKeyToken` atributos e. Se ambos os atributos corresponderem entre dois elementos dentro de um manifesto, a análise do manifesto não terá sucesso.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauções ao alterar manualmente os manifestos ou aplicativos  
 Ao atualizar um manifesto de aplicativo, você deve assinar novamente o manifesto do aplicativo e o manifesto de implantação. O manifesto de implantação contém uma referência ao manifesto do aplicativo que inclui o hash do arquivo e sua assinatura digital.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Precauções com o uso do provedor de implantação  
 O [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto de implantação tem uma `deploymentProvider` propriedade que aponta para o caminho completo do local de onde o aplicativo deve ser instalado e atendido:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Esse caminho é definido quando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] o cria o aplicativo e é obrigatório para aplicativos instalados. O caminho aponta para o local padrão onde o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalador instalará o aplicativo e procurará por atualizações. Se você usar o comando **xcopy** para copiar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo para um local diferente, mas não alterar a `deploymentProvider` propriedade, o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ainda fará referência ao local original quando tentar baixar o aplicativo.  
  
 Se você quiser mover ou copiar um aplicativo, também deverá atualizar o `deploymentProvider` caminho, para que o cliente realmente instale a partir do novo local. A atualização desse caminho é principalmente uma preocupação se você tiver instalado aplicativos. Para aplicativos online que são sempre iniciados por meio da URL original, a definição de `deploymentProvider` é opcional. Se `deploymentProvider` for definido, ele será respeitado; caso contrário, a URL usada para iniciar o aplicativo será usada como a URL base para baixar os arquivos do aplicativo.  
  
> [!NOTE]
> Sempre que atualizar o manifesto, você também deverá reconectá-lo novamente.  
  
## <a name="see-also"></a>Consulte Também  
 [Solucionando problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
