---
title: Opções de linha de comando do devenv para desenvolvimento de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185274"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Opções de linha de comando devenv para desenvolvimento de VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite que os desenvolvedores automatizem tarefas da linha de comando ao executar devenv.exe, o arquivo que inicia o IDE (ambiente de desenvolvimento integrado) do Visual Studio.  
  
 As tarefas incluem:  
  
- Implantação de aplicativos em configurações predefinidos de fora do IDE.  
  
- Criando projetos automaticamente usando configurações de compilação predefinidas ou configurações de depuração.  
  
- Carregar o IDE em configurações específicas, tudo de fora do IDE. Além disso, você pode personalizar o IDE na inicialização.  
  
## <a name="guidelines-for-switches"></a>Diretrizes para opções  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a documentação descreve as opções de linha de comando devenv de nível de usuário. Para obter mais informações, consulte [Opções de linha de comando do devenv](../ide/reference/devenv-command-line-switches.md). O devenv também dá suporte a opções de linha de comando adicionais que são úteis com o desenvolvimento, a implantação e a depuração do VSPackage.  
  
|Opção de linha de comando|Descrição|  
|--------------------------|-----------------|  
|/safemode|É iniciado [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no modo de segurança, carregando apenas o IDE e os serviços padrão. A opção/safemode impede que todas as VSPackages de terceiros sejam carregadas quando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é iniciado, garantindo assim a execução estável.<br /><br /> Esta opção não aceita nenhum argumento.|  
|/resetskippkgs|Limpa todas as opções de ignorar carregamento que foram adicionadas por usuários que desejam evitar o carregamento de VSPackages problemáticas e, em seguida, inicia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . A presença de uma marca SkipLoading desabilita o carregamento de um VSPackage. Limpar a marca habilita novamente o carregamento do VSPackage.<br /><br /> Esta opção não aceita nenhum argumento.|  
|/rootsuffix|Inicia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando um local alternativo. O comando a seguir é executado pelo atalho criado pelo [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] instalador:<br /><br /> devenv/RootSuffix exp<br /><br /> Nesse caso, exp identifica um local com um sufixo específico, por exemplo, 10.0 Exp em vez de 10,0. A instância experimental permite que você depure um VSPackage separadamente da instância do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que você está usando para escrever código.<br /><br /> Essa opção pode usar qualquer cadeia de caracteres que identifique um local que você criou usando VSRegEx.exe. Para obter mais informações, consulte [a instância experimental](../extensibility/the-experimental-instance.md).|  
|/splash|Mostra a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tela inicial como de costume e, em seguida, mostra uma caixa de mensagem antes de mostrar o IDE principal. A caixa de mensagem permite que você estude a tela inicial para verificar um ícone de produto VSPackage, por exemplo.<br /><br /> Esta opção não aceita nenhum argumento.|  
  
## <a name="see-also"></a>Consulte Também  
 [Adicionando opções de linha de comando](../extensibility/adding-command-line-switches.md)   
 [Opções de linha de comando do desenvolvedor](../ide/reference/devenv-command-line-switches.md)
