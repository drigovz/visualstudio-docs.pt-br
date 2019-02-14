---
title: Usar parâmetros de linha de comando para instalar o Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cd61d03b5639038612e305697f4245e582ee3efe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794033"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usar parâmetros de linha de comando para instalar o Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio 2017, consulte [usar parâmetros de linha de comando para instalar o Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Ao instalar o Visual Studio 2015 por meio de um prompt de comando, é possível usar os parâmetros de linha de comando a seguir (também conhecidos como opções).

> [!NOTE]
>  Certifique-se de que você use o instalador real e não o arquivo de bootstrapper. Por exemplo, verifique se você usar **`vs_enterprise.exe`** em vez de vs_enterprise_*GUID*.exe. Você pode baixar um instalador de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Lista de parâmetros de linha de comando
 Parâmetros de linha de comando do Visual Studio não diferenciam maiúsculas de minúsculas.

|Parâmetro|Descrição|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|Exibe parâmetros de linha de comando.|
|**/AddRemoveFeatures**|Especifica que recursos adicionar ou remover do produto instalado.|
|**/AdminFile** *AdminDeployment.xml*|Instala o Visual Studio usando o arquivo de dados que você especificou para instalação administrativa.|
|**/ChainingPackage** *BundleName*|Especifica qual pacote está encadeando esse conjunto. Também pode ser usado para especificar um coorte de aprimoramento de experiência do cliente.|
|**/Createadminfile \<filename >**|Especifica o local para criar um arquivo de controle que pode ser usado com /AdminFile|
|**/CustomInstallPath** *InstallationDirectory*|Instala todos os pacotes que podem ser redestinados no diretório que você especifica.|
|**/ForceRestart**|Sempre reinicia o computador após a instalação.|
|**/full**|Instala todos os recursos do produto.|
|**/InstallSelectableItems \<item name 1>[;\<item name 2>]**|Lista de itens da árvore de seleção para verificação na tela de seleção do Assistente de instalação.|
|**/l**<br /><br /> **/Log** *Filename*|Especifica um local para o arquivo de log.|
|**/layout** *diretório*|Copia os arquivos da mídia de instalação no diretório que você especifica.|
|**/NoCacheOnlyMode**|Impede pré-população do cache de pacote.|
|**/NoRefresh**|Impede que a verificação de versões mais recentes do produto para versões atualizadas obrigatórias ou recomendadas.|
|**/norestart**|Impede que o aplicativo de instalação reinicie o computador durante ou após a instalação. Consulte a seção códigos de retorno de [guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md) para os códigos de retorno a ser procurado.|
|**/noweb**|Impede a instalação da Internet.|
|**/OverrideFeedUri \<path to feed file>**|Caminho até um feed local e externo que descreve os itens de software|
|**/ProductKey**<br /><br /> *ProductKey*|Define uma chave de produto personalizada sem traços e com até 25 caracteres.|
|**/PromptRestart**|Avisa o usuário antes de reiniciar o computador.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Suprime a interface de usuário para o aplicativo de instalação. Se o Visual Studio já estiver instalado e você não especificar outros parâmetros além desse, o aplicativo de instalação será executado no Modo de Manutenção.|
|**/qb**<br /><br /> **/passive**|Mostra o andamento, mas não aguarda a entrada do usuário.|
|**/repair**|Repara o Visual Studio.|
|**/SuppressRefreshPrompt**|Impede a exibição que a caixa de diálogo disponíveis de atualização no Assistente de instalação, assim, o Assistente de instalação aceitará automaticamente qualquer versão atualizada necessários ou recomendados.|
|**/u**<br /><br /> **/Uninstall**|Desinstala o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/Uninstall /Force**<br /><br /> **/u /force**|Desinstala o Visual Studio e todos os recursos que são compartilhados com outros produtos. **Aviso:** se você usar esse parâmetro, outros produtos que estão instalados no mesmo computador podem parar de funcionar corretamente.|

## <a name="see-also"></a>Consulte também
 [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md)