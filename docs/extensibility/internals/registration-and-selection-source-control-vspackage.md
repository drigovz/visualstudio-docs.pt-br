---
title: Inscrição e Seleção (Source Control VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705716"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro e seleção (VSPackage do controle do código-fonte)
Um controle de origem VSPackage deve ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registrado para expô-lo ao . Se mais de um controle de origem VSPackage estiver registrado, o usuário poderá selecionar qual VSPackage carregará em momentos apropriados. Consulte [VSPackages](../../extensibility/internals/vspackages.md) para obter mais detalhes sobre VSPackages e como registrá-los.

## <a name="registering-a-source-control-package"></a>Registrando um pacote de controle de origem
 O pacote de controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é registrado para que o ambiente possa encontrá-lo e consultar seus recursos suportados. Isso está de acordo com um esquema de carregamento de atraso no qual uma instância de um pacote é criada apenas quando seus recursos ou comandos são necessários ou solicitados explicitamente.

 O VSPackages coloca as informações em uma chave de registro\\específica da versão, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, onde *X* é o número da versão principal e *Y* é o número da versão menor. Essa prática fornece a capacidade de suportar a instalação [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lado a lado de várias versões de .

 A [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário (UI) suporta a seleção entre vários plug-ins de controle de origem instalados (através do Pacote adaptador de controle de fonte) bem como o controle de origem VSPackages. Só pode haver um plug-in de controle de origem ativo ou VSPackage por vez. No entanto, como descrito abaixo, o IDE permite alternar entre plug-ins de controle de origem e VSPackages através de um mecanismo automático de troca de pacotes baseado em soluções. Existem alguns requisitos por parte do controle de origem VSPackage para habilitar este mecanismo de seleção.

### <a name="registry-entries"></a>Entradas do Registro
 Um pacote de controle de origem precisa de três GUIDs privados:

- Guia do pacote: Este é o guid principal para o pacote que contém a implementação do controle de origem (chamado ID_Package nesta seção).

- Controle de origem GUID: Este é um GUID para o controle de origem VSPackage usado para registrar-se no Visual Studio Source Control Stub e também é usado como um guid de contexto de interface do ar de comando. O guid do serviço de controle de origem está registrado sob o GUID de controle de origem. No exemplo, o GUID de controle de origem é chamado de ID_SccProvider.

- Serviço de controle de origem GUID: Este é o serviço privado GUID usado pelo Visual Studio (chamado SID_SccPkgService nesta seção). Além disso, o pacote de controle de origem precisa definir outros GUIDs para VSPackages, janelas de ferramentas e assim por diante.

  As seguintes entradas de registro devem ser feitas por um vsPackage de controle de origem:

| Nome da chave | Entradas |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (padrão) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (padrão) =\<rg_sz: Nome amigável do Pacote><br /><br /> Serviço = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (padrão) = rg_sz:#\<ID de recursos para> de nome localizado<br /><br /> Pacote = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Observe que o `SourceCodeControl`nome da chave, , já é usado e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não está disponível como opção para \<PackageName>.) | (padrão) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Selecionando um pacote de controle de origem
 Vários plug-ins baseados em API de controle de fonte e vsPackages de controle de origem podem ser registrados simultaneamente. O processo de seleção de um plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de controle de origem ou VSPackage deve garantir que carregue o plug-in ou VSPackage no momento apropriado e possa adiar o carregamento de componentes desnecessários até que sejam necessários. Além disso, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve remover todas as idas de ui de outros VSPackages inativos, incluindo itens de menu, caixas de diálogo e barras de ferramentas, e exibir a ui para o VSPackage ativo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carrega um vsPackage de controle de origem quando qualquer uma das seguintes operações é realizada:

- A solução é aberta (quando a solução está sob controle de origem).

   Quando uma solução ou projeto sob controle de origem é aberto, o IDE faz com que o controle de origem VSPackage que foi designado para que essa solução seja carregada.

- Qualquer um dos comandos de menu do controle de origem VSPackage é executado.

  Um controle de origem VSPackage deve carregar todos os componentes de que precisa apenas quando eles realmente serão usados (também conhecido como carregamento atrasado).

### <a name="automatic-solution-based-vspackage-swapping"></a>Troca automática de pacotes VS baseado em solução
 Você pode trocar manualmente o controle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de origem VSPackages através da caixa de diálogo **Opções** na categoria **Controle de** origem. A troca automática de pacotes baseada em soluções significa que um pacote de controle de origem designado para uma determinada solução é automaticamente definido como ativo quando essa solução é aberta. Todos os pacotes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>de controle de origem devem ser implementados e . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lida com o switch entre plug-ins de controle de origem (implementando a API plug-in de controle de fonte) e vsPackages de controle de origem.

 O pacote adaptador de controle de origem é usado para alternar para qualquer plug-in baseado em API plug-in de controle de fonte. O processo de mudança para o pacote intermediário do adaptador de controle de fonte e determinar qual plug-in de controle de origem deve ser definido como ativo ou inativo é transparente para o usuário. O pacote adaptador está sempre ativo quando qualquer plug-in de controle de origem está ativo. Alternar entre dois plug-ins de controle de origem equivale a simplesmente carregar e descarregar o DLL plug-in. Mudar para um controle de origem VSPackage, no entanto, envolve interagir com o IDE para carregar o VSPackage apropriado.

 Um controle de origem VSPackage é chamado quando qualquer solução é aberta e a chave de registro para o VSPackage está no arquivo de solução. Quando a solução [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é aberta, encontra o valor do registro e carrega o controle de origem apropriado VSPackage. Todos os VSPackages de controle de origem devem ter as entradas de registro descritas acima. Uma solução que está sob controle de origem é marcada como sendo associada a um determinado controle de origem VSPackage. Controle de origem Os <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> VSPackages devem implementar o para habilitar a troca automática de VSPackage baseada em solução.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio UI para seleção e comutação de pacotes
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornece uma ui para controle de origem VSPackage e seleção de plug-in na caixa de diálogo **Opções** na categoria **Controle de** origem. Ele permite que o usuário selecione o plug-in de controle de origem ativo ou VSPackage. Uma lista de paradas inclui:

- Todos os pacotes de controle de origem instalados

- Todos os plug-ins de controle de origem instalados

- Uma opção "nenhum", que desativa o controle de código fonte

  Apenas a ui para a escolha de controle de origem ativa é visível. A seleção VSPackage oculta a ida e rei para o VSPackage anterior e mostra a iu para o novo. O VSPackage ativo é selecionado por usuário. Se um usuário tiver [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] várias cópias de aberto simultaneamente, cada uma pode potencialmente usar um VSPackage ativo diferente. Se vários usuários estiverem conectados ao mesmo computador, cada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usuário poderá ter instâncias separadas de abertura, cada uma com um VSPackage ativo diferente. Quando várias [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instâncias de um usuário são fechadas, o controle de origem VSPackage que estava ativo para a última solução aberta torna-se o controle de origem padrão VSPackage, a ser definido ativo na reinicialização.

  Ao contrário [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]das versões anteriores de , uma reinicialização do IDE não é mais a única maneira de alternar o controle de origem VSPackages. A seleção do VSPackage é automática. A comutação de pacotes requer privilégios do Usuário do Windows (não administrador ou usuário de energia).

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Recursos](../../extensibility/internals/source-control-vspackage-features.md)
- [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
