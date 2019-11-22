---
title: Guia do Administrador do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295918"
---
# <a name="visual-studio-administrator-guide"></a>Guia do Administrador do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre o Visual Studio, consulte o [Guia do administrador do Visual Studio](/visualstudio/install/visual-studio-administrator-guide).

Você pode implantar o Visual Studio 2015 em uma rede desde que cada computador de destino atenda aos [requisitos mínimos de instalação](https://visualstudio.microsoft.com/vs/older-downloads/). Crie um compartilhamento de rede executando o arquivo de instalação com a opção /layout (conforme descrito na página [Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)) e, em seguida, copiando-o do computador local para o compartilhamento de rede. Se você estiver usando um ISO, poderá montar o ISO e compartilhá-lo ou copiar o ISO para um compartilhamento de rede.  
  
 Observe que as instalações de um compartilhamento de rede "lembram" o local de origem do qual vieram. Isso significa que um reparo de um computador cliente pode ter que retornar para o compartilhamento de rede do qual o cliente foi instalado originalmente. Escolha o local de rede cuidadosamente para que ele se alinhe ao tempo de vida que você espera ter os clientes do Visual Studio 2015 em execução na sua organização.  
  
## <a name="detection-and-servicing-keys"></a>Chaves de detecção e de serviço  
 Você pode usar subchaves de detecção no registro para determinar se um produto do Visual Studio já está instalado em um computador. Você usaria essas chaves de detecção em uma implantação automatizada para determinar se era necessário continuar com uma instalação.  Consulte [detectando requisitos do sistema](../extensibility/internals/detecting-system-requirements.md)[detectando requisitos do sistema].  
  
## <a name="avoiding-reboots"></a>Evitando reinicializações  
 Você pode reduzir as reinicializações, certificando-se de atender aos pré-requisitos apropriados do Visual Studio antes de implantar o Visual Studio. Para o .NET Framework, talvez seja necessário reinicializar os computadores que executam o Windows 8 se você implantar o Visual Studio 2015 neles sem primeiro instalar o .NET Framework 4,6.  
  
 Para a emulação de dispositivo Android e Windows, talvez seja necessário reinicializar os computadores se você ainda não tiver o recurso do Windows Hyper-V ativado. Para o desenvolvimento para a Web, talvez seja necessário reinicializar os computadores se você ainda não tiver o servidor Web de recursos do Windows ativado. Para o desenvolvimento do Office, talvez seja necessário reinicializar os computadores se você ainda não tiver o recurso do Windows identificar a base ativada. Reinicialize os computadores se você ainda não tiver o servidor Web de recursos do Windows ativado. Para o desenvolvimento do Office, talvez seja necessário reinicializar os computadores se você ainda não tiver o recurso do Windows identificar a base ativada. Para saber mais sobre como automatizar a detecção e a instalação de recursos do Windows, consulte [instalando uma função de servidor em um servidor que executa uma instalação Server Core do Windows server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Códigos de Retorno de Erro  
 A tabela a seguir lista os códigos de erro importantes. Você pode usar esses códigos de erro em sua automação para decidir se uma reinicialização é necessária e se a instalação foi bem-sucedida. Se você receber um código de erro, considere as etapas de solução de problemas na página [instalar o Visual Studio](../install/install-visual-studio-2015.md) .  
  
|Status da instalação|Reinicialização não necessária|Reinicialização necessária|Descrição|  
|------------------|--------------------------|----------------------|-----------------|  
|Êxito|0x00000000 [0]|0x00000bc2 [3010]|Instalação bem-sucedida.|  
|Bloco|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Se o único bloco a ser relatado for "Reinicialização Pendente", o valor retornado será o valor Reinicialização Incompleta Necessária (0x80048bc7).|  
|Cancelar|0x00000642 [1602]|0x80048642 [-2147187134]|Quando o valor de reinicialização é retornado, o código de retorno é 1602.|  
|Reinicialização incompleta necessária|N/D|0x80048bc7 [-2147185721]|A reinicialização é necessária antes de continuar a instalação.|  
|Falha|0x00000643 [1603]|0x80048643 [-2147187133]|Quando o valor de reinicialização é retornado, o código de retorno é 1603.|  
  
## <a name="interactive-administrator-installer"></a>Instalador de administrador interativo  
 Se você estiver criando um instalador interativo sobre a instalação do Visual Studio, poderá exibir o progresso do instalador do Visual Studio. O instalador do Visual Studio 2015 é baseado na tecnologia de encadeamento do WiX (software livre Windows Installer XML), também conhecida como "gravação". A tecnologia de gravação dá suporte a dois protocolos de comunicação: Burn e netfx4. Para obter uma referência resumida, consulte a descrição do atributo Protocol na documentação do elemento ExePackage em [wixtoolset.org](https://wixtoolset.org/). Uma revisão da implementação do código-fonte aberto do WiX desse atributo de protocolo pode ser necessária para a integração.  
  
## <a name="controlling-what-is-installed"></a>Controlando o que está instalado  
 Se você quiser controlar o que o usuário final pode instalar, há duas opções: a instalação do arquivo do administrador e as opções de linha de comando. Selecione o arquivo de administrador instalar se seu objetivo for restringir o que o usuário final pode escolher de sua experiência do instalador do Visual Studio. Selecione os parâmetros de linha de comando se desejar criar uma configuração inicial, mas permitir que o usuário final escolha sua própria experiência do instalador do Visual Studio.  
  
 Para obter mais informações sobre a experiência de arquivo do administrador, consulte [como: criar e executar uma instalação autônoma do Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) e [como aplicar automaticamente as chaves do produto ao implantar o Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Para obter mais informações sobre os controles de linha de comando, consulte a página [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .  
  
## <a name="specifying-customer-feedback-settings"></a>Especificar as configurações de comentários do cliente  

Por padrão, a instalação do Visual Studio habilita os comentários do cliente. Você pode configurar o Visual Studio para desabilitar os comentários dos clientes em computadores individuais, alterando o valor da seguinte chave do registro para a cadeia de caracteres "0":  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
(Por exemplo, altere-o para HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SQM Optin = "0")  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Como instalar uma versão específica do Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Descreve como instalar configurações específicas da versão atual do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Como criar e executar uma instalação autônoma do Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Descreve como instalar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no modo autônomo.|  
|[Como aplicar as chaves de produto automaticamente durante a implantação do Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Descreve como aplicar chaves de produto ao implantar em vários computadores.|  
|[Guia do administrador do Help Viewer](../ide/help-viewer-administrator-guide.md)|Fornece informações sobre como gerenciar instalações de ajuda local para ambientes de rede que têm ou não têm acesso à Internet.|  
|[Instalar o Visual Studio](../install/install-visual-studio-2015.md)|Fornece instruções e links para tópicos que descrevem como instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|