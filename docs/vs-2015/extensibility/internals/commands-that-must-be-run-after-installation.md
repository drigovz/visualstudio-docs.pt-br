---
title: Comandos que devem ser executados após a instalação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838662"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que precisam ser executados após a instalação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Se você implantar sua extensão por meio de um arquivo. msi, deverá executar `devenv /setup` como parte da instalação para que o Visual Studio descubra suas extensões.  
  
> [!NOTE]
> As informações neste tópico se aplicam à localização do DevEnv com o Visual Studio 2008 e anterior. Para obter informações sobre como descobrir o DevEnv com versões posteriores do Visual Studio, consulte [detectando requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Localizando devenv.exe  
 Você pode localizar as devenv.exe de cada versão de valores de registro que os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] instaladores gravam, usando a tabela RegLocator e a tabela AppSearch para armazenar os valores do registro como propriedades. Para obter mais informações, consulte [detectando requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator linhas da tabela para localizar devenv.exe de diferentes versões do Visual Studio  
  
|Signature_|Root|Chave|Nome|Tipo|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Linhas da tabela AppSearch para linhas da tabela RegLocator correspondentes  
  
|Propriedade|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Por exemplo, o instalador do Visual Studio grava o valor do registro de **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** como **C:\VS2008\Common7\IDE\devenv.exe**, um caminho completo para o executável que o instalador deve executar.  
  
 **Observação** Como a coluna de tipo RegLocator é 2, não é necessário especificar informações de versão adicionais na tabela de assinatura.  
  
## <a name="running-devenvexe"></a>Executando devenv.exe  
 Depois que a ação AppSearch padrão for executada no instalador, cada propriedade na tabela AppSearch terá um valor que aponta para o arquivo de devenv.exe para a versão correspondente do Visual Studio. Se qualquer um dos valores de registro especificados não estiver presente — porque essa versão do Visual Studio não está instalada — a propriedade especificada será definida como NULL.  
  
 O Windows Installer dá suporte à execução de um executável no qual uma propriedade aponta por meio do tipo de ação personalizada 50. A ação personalizada deve incluir as opções de execução em script, msidbCustomActionTypeInScript (1024) e msidbCustomActionTypeCommit (512), para garantir que o VSPackage tenha sido instalado com êxito antes de integrá-lo ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Para obter mais informações, consulte tabela de CustomAction e opções de execução em script de ação personalizada.  
  
 Ações personalizadas do tipo 50 especificam a propriedade que contém o executável como o valor da coluna de origem e os argumentos de linha de comando na coluna de destino.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Linhas da tabela CustomAction a serem executadas devenv.exe  
  
|Ação|Tipo|Fonte|Destino|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 As ações personalizadas devem ser criadas na tabela InstallExecuteSequence para agendá-las para execução durante a instalação. Use a propriedade correspondente em cada linha da coluna condição para impedir que a ação personalizada seja executada se essa versão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] não estiver instalada no sistema.  
  
> [!NOTE]
> `Null` as propriedades são avaliadas como `False` quando usadas em condições.  
  
 O valor da coluna de sequência para cada ação personalizada depende de outros valores de sequência em seu pacote de Windows Installer. Os valores de sequência devem ser de modo que o devenv.exe ações personalizadas sejam executadas o mais próximo possível imediatamente antes da ação InstallFinalize padrão.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabela InstallExecuteSequence para agendar as ações personalizadas de devenv.exe  
  
|Ação|Condição|Sequência|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Consulte Também  
 [Instalando VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
