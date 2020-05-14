---
title: Comandos que devem ser executados após a instalação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709481"
---
# <a name="commands-that-must-be-run-after-installation"></a>Comandos que devem ser executados após a instalação
Se você implantar sua extensão através de um arquivo *.msi,* você **devenv /configuração** como parte de sua instalação para que o Visual Studio descubra suas extensões.

> [!NOTE]
> As informações neste tópico se aplicam a encontrar *devenv.exe* com o Visual Studio 2008 e anteriormente. Para obter informações sobre como descobrir *devenv.exe* com versões posteriores do Visual Studio, consulte [Detectar requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Encontre devenv.exe
 Você pode localizar o *devenv.exe* de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cada versão a partir dos valores de registro que os instaladores escrevem, usando a tabela RegLocator e as tabelas AppSearch para armazenar os valores de registro como propriedades. Para obter mais informações, consulte [Detectar requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Linhas de tabela regLocator para localizar devenv.exe de diferentes versões do Visual Studio

|Assinatura|Root|Chave|Nome|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Configuração\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Configuração\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Configuração\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Configuração\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Linhas de tabela do AppSearch para as linhas de tabela reglocator correspondentes

|Propriedade|Assinatura|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Por exemplo, o instalador do Visual Studio grava o valor de registro de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Configuração\\AmbientePath** como *C:\VS2008\Common7\IDE\devenv.exe,* um caminho completo para o executável que o instalador deve executar.

> [!NOTE]
> Como a coluna Tipo da tabela RegLocator é 2, não é necessário especificar informações adicionais da versão na tabela Assinatura.

## <a name="run-devenvexe"></a>Executar devenv.exe
 Depois que a ação padrão do AppSearch é executada no instalador, cada propriedade na tabela AppSearch tem um valor apontando para o arquivo *devenv.exe* para a versão correspondente do Visual Studio. Se algum dos valores de registro especificados não estiver presente — porque essa versão do Visual Studio não estiver instalada — a propriedade especificada será definida como nula.

 O Windows Installer suporta a execução de um executável para o qual uma propriedade aponta através do tipo de ação personalizada 50. A ação personalizada deve incluir as `msidbCustomActionTypeInScript` opções de execução `msidbCustomActionTypeCommit` no script (1024) e (512), para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]garantir que o VSPackage tenha sido instalado com sucesso antes de integrá-lo em . Para obter mais informações, consulte [a tabela CustomAction](/windows/desktop/msi/customaction-table) e [as opções de execução de ação personalizadas no script](/windows/desktop/msi/custom-action-in-script-execution-options).

 As ações personalizadas do tipo 50 especificam a propriedade que contém o executável como o valor da coluna Origem e os argumentos da linha de comando na coluna Destino.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Linhas de tabela CustomAction para executar devenv.exe

|Ação|Type|Fonte|Destino|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/configuração|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/configuração|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/configuração|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/configuração|

 As ações personalizadas devem ser incorporadas na tabela InstallExecuteSequence para agendar a execução durante a instalação. Use a propriedade correspondente em cada linha da coluna Condição para evitar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que a ação personalizada seja executada se essa versão não estiver instalada no sistema.

> [!NOTE]
> Propriedades de valor `False` nulo avaliam quando usadas em condições.

 O valor da coluna Seqüência para cada ação personalizada depende de outros valores de seqüência no pacote do Instalador do Windows. Os valores de seqüência devem ser tais que as ações *personalizadas devenv.exe* sejam executadas o mais próximo possível de imediatamente antes da ação padrão InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Instaleaaaa tabelaExecutepara agendar as ações personalizadas devenv.exe

|Ação|Condição|Sequência|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Confira também
- [Instale vspackages com o instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
