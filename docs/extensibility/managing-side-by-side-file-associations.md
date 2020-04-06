---
title: Gerenciando associações de arquivos lado a lado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702754"
---
# <a name="manage-side-by-side-file-associations"></a>Gerenciar associações de arquivos lado a lado

Se o VSPackage fornecer associações de arquivos, você deve decidir como lidar com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalações lado a lado nas quais uma determinada versão deve ser invocada para abrir um arquivo. Formatos de arquivo incompatíveis compõem o problema.

Os usuários esperam que uma nova versão de um produto seja compatível com versões anteriores, para que os arquivos existentes possam ser carregados em uma nova versão sem perder dados. Idealmente, seu VSPackage pode carregar e salvar os formatos de arquivo de versões anteriores. Se isso não for verdade, você deve oferecer para atualizar o formato do arquivo para a nova versão do seu VSPackage. A desvantagem dessa abordagem é que o arquivo atualizado não pode ser aberto na versão anterior.

Para evitar esse problema, você pode alterar extensões quando os formatos de arquivo se tornarem incompatíveis. Por exemplo, a versão 1 do vsPackage poderia usar a extensão, *.mypkg10*, e a versão 2 poderia usar a extensão, *.mypkg20*. Essa diferença identifica o VSPackage que abre um arquivo específico. Se você adicionar vspackages mais novos à lista de programas associados a uma extensão antiga, os usuários podem clicar com o botão direito do mouse no arquivo e optar por abri-lo em um VSPackage mais novo. Nesse ponto, o VSPackage pode oferecer para atualizar o arquivo para o novo formato ou abrir o arquivo e manter a compatibilidade com as versões anteriores do VSPackage.

> [!NOTE]
> Você pode combinar essas abordagens. Por exemplo, você pode oferecer compatibilidade retrógrada carregando um arquivo mais antigo e oferecer para atualizar o formato do arquivo quando o usuário o salva.

## <a name="face-the-problem"></a>Enfrentar o Problema

Se você quiser que vários VSPackages lado a lado usem a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mesma extensão, você deve escolher a versão disso associada à extensão. Aqui estão duas alternativas:

- Abra o arquivo na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versão mais recente do instalado no computador do usuário.

   Nesta abordagem, o instalador é responsável por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] determinar a versão mais recente e incluí-lo na entrada de registro escrita para a associação de arquivos. Em um pacote do Windows Installer, você pode incluir ações [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]personalizadas para definir uma propriedade que indique a versão mais recente de .

  > [!NOTE]
  > Neste contexto, "mais recente" significa "versão suportada mais recente". Essas entradas do instalador não detectarão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automaticamente uma versão subseqüente de . As entradas na [detecção de requisitos do sistema](../extensibility/internals/detecting-system-requirements.md) e em [comandos que devem ser executados após](../extensibility/internals/commands-that-must-be-run-after-installation.md) a instalação são semelhantes às apresentadas aqui e são necessárias para suportar versões adicionais de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   As linhas a seguir na tabela CustomAction definiram a propriedade DEVENV_EXE_LATEST como sendo uma propriedade definida pelas tabelas AppSearch e RegLocator discutidas em [Comandos que devem ser executados após a instalação](../extensibility/internals/commands-that-must-be-run-after-installation.md). As linhas na tabela InstallExecuteSequence agendam as ações personalizadas no início da seqüência de execução. Valores na coluna Condição fazem a lógica funcionar:

  - Visual Studio .NET 2002 é a versão mais recente se for a única versão presente.

  - Visual Studio .NET 2003 é a versão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mais recente somente se estiver presente e não estiver presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]é a versão mais recente se for a única versão presente.

    O resultado líquido é que DEVENV_EXE_LATEST contém o caminho da versão mais recente do devenv.exe.

  **Linhas de tabela CustomAction que determinam a versão mais recente do Visual Studio**

  |Ação|Type|Fonte|Destino|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Instalelinhas de tabelaExecute que determinam a versão mais recente do Visual Studio**

  |Ação|Condição|Sequência|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 E NÃO (DEVENV_EXE_2003 ou DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 e não DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Você pode usar a propriedade DEVENV_EXE_LATEST na tabela Registro do pacote Windows Installer para escrever o valor padrão da chave ***HKEY_CLASSES_ROOT ProgId*ShellOpenCommand,** [DEVENV_EXE_LATEST] "%1"

- Execute um programa de launcher compartilhado que pode fazer a melhor escolha das versões disponíveis do VSPackage.

   Os desenvolvedores [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] escolheram essa abordagem para lidar com os requisitos complexos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dos múltiplos formatos de soluções e projetos que resultam de muitas versões de . Nesta abordagem, você registra um programa de launcher como manipulador de extensão. O launcher examina o arquivo e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] decide qual versão e seu VSPackage pode lidar com esse arquivo em particular. Por exemplo, se um usuário abrir um arquivo que foi salvo pela última vez por uma versão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]específica do vsPackage, o launcher poderá iniciar esse VSPackage na versão correspondente de . Além disso, um usuário pode configurar o launcher para sempre iniciar a versão mais recente. Um launcher também pode solicitar ao usuário que atualize o formato do arquivo. Se o formato do arquivo incluir um número de versão, o launcher poderá informar um usuário se o formato do arquivo for de uma versão posterior a um ou mais dos VSPackages instalados.

   O launcher deve estar em um componente do Windows Installer que é compartilhado com todas as versões do seu VSPackage. Este processo garante que a versão mais recente esteja sempre instalada e não seja removida até que todas as versões do vsPackage sejam desinstaladas. Desta forma, as associações de arquivos e outras entradas de registro do componente launcher são preservadas mesmo que uma versão do VSPackage seja desinstalada.

## <a name="uninstall-and-file-associations"></a>Desinstalar e arquivar associações

A desinstalação de um VSPackage que grava entradas de registro para associações de arquivos remove as associações de arquivos. Portanto, a extensão não possui programas associados. O Windows Installer não "recupera" as entradas de registro que foram adicionadas quando o VSPackage foi instalado. Aqui estão algumas maneiras de corrigir as associações de arquivos de um usuário:

- Use um componente de lançador compartilhado como descrito anteriormente.

- Instrua o usuário a executar um reparo da versão do VSPackage que o usuário deseja possuir a associação de arquivos.

- Forneça um programa executável separado que reescreva as entradas de registro apropriadas.

- Forneça uma página de opções de configuração ou caixa de diálogo que permite que os usuários escolham associações de arquivos e recuperem associações perdidas. Instrua os usuários a executá-lo após a desinstalação.

## <a name="see-also"></a>Confira também

- [Registre extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registre verbos para extensões de nome de arquivo](../extensibility/registering-verbs-for-file-name-extensions.md)
