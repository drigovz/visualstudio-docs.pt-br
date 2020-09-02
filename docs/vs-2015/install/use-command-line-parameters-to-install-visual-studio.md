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
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180254"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usar parâmetros de linha de comando para instalar o Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre o Visual Studio, consulte [usar parâmetros de linha de comando para instalar o Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Ao instalar o Visual Studio 2015 por meio de um prompt de comando, é possível usar os parâmetros de linha de comando a seguir (também conhecidos como opções).

> [!NOTE]
> Certifique-se de usar o instalador real e não o arquivo bootstrapper. Por exemplo, certifique-se **`vs_enterprise.exe`** de usar em vez de Vs_enterprise_*GUID*. exe. Você pode baixar um instalador do [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Lista de parâmetros de linha de comando

Parâmetros de linha de comando do Visual Studio não diferenciam maiúsculas de minúsculas.

|Parâmetro|Descrição|
|---------------|-----------------|
|**/?**<br /><br /> **/Help**<br /><br /> **/h**|Exibe parâmetros de linha de comando.|
|**/AddRemoveFeatures**|Especifica que recursos adicionar ou remover do produto instalado.|
|**/AdminFile** *AdminDeployment.xml*|Instala o Visual Studio usando o arquivo de dados que você especificou para instalação administrativa.|
|**/ChainingPackage** *BundleName*|Especifica qual pacote está encadeando esse conjunto. Também pode ser usado para especificar uma experiência de aperfeiçoamento do cliente coorte.|
|**/CreateAdminFile \<filename>**|Especifica o local para criar um arquivo de controle que pode ser usado com/AdminFile|
|**/CustomInstallPath** *InstallationDirectory*|Instala todos os pacotes que podem ser redestinados no diretório que você especifica.|
|**/ForceRestart**|Sempre reinicia o computador após a instalação.|
|**/full**|Instala todos os recursos do produto.|
|**/Installselectableitems. \<item name 1> [; \<item name 2> ]**|Lista de itens de árvore de seleção a serem verificados na tela de seleção do assistente do instalador.|
|**/l**<br /><br /> **/Log** *Nome do arquivo* /log|Especifica um local para o arquivo de log.|
|**/layout** *diretório* /layout|Copia os arquivos da mídia de instalação no diretório que você especifica.|
|**/NoCacheOnlyMode**|Impede pré-população do cache de pacote.|
|**/NoRefresh**|Impede a verificação de versões mais recentes deste produto para as versões atualizadas obrigatórias ou recomendadas.|
|**/norestart**|Impede que o aplicativo de instalação reinicie o computador durante ou após a instalação. Consulte a seção códigos de retorno do [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md) para obter os códigos de retorno a serem procurados.|
|**/noweb**|Impede a instalação da Internet.|
|**/OverrideFeedUri \<path to feed file>**|Caminho para um feed local e externo que descreve os itens de software|
|**/ProductKey**<br /><br /> *ProductKey*|Define uma chave de produto personalizada sem traços e com até 25 caracteres.|
|**/PromptRestart**|Avisa o usuário antes de reiniciar o computador.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/Silent**|Suprime a interface de usuário para o aplicativo de instalação. Se o Visual Studio já estiver instalado e você não especificar outros parâmetros além desse, o aplicativo de instalação será executado no Modo de Manutenção.|
|**/qb**<br /><br /> **/Passive**|Mostra o andamento, mas não aguarda a entrada do usuário.|
|**/Repair**|Repara o Visual Studio.|
|**/SuppressRefreshPrompt**|Impede a exibição da caixa de diálogo atualizar disponível no assistente de instalação, portanto, o assistente de instalação aceitará automaticamente todas as versões atualizadas necessárias ou recomendadas.|
|**/u**<br /><br /> **/Uninstall**|Desinstala o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/Uninstall/Force**<br /><br /> **/u /force**|Desinstala o Visual Studio e todos os recursos que são compartilhados com outros produtos. **AVISO:**  Se você usar esse parâmetro, outros produtos instalados no mesmo computador poderão parar de funcionar corretamente.|

## <a name="see-also"></a>Consulte Também

- [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md)