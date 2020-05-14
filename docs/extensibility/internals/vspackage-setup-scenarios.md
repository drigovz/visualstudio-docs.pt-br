---
title: Cenários de configuração de pacotes VS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703982"
---
# <a name="vspackage-setup-scenarios"></a>Cenários de instalação do VSPackage

É importante projetar seu instalador VSPackage para obter flexibilidade. Por exemplo, você pode precisar liberar um patch de segurança no futuro, ou pode mudar uma estratégia de negócios que requer suporte completo de versão lado a lado.

Em [Suporte a várias versões do Visual Studio,](../../extensibility/supporting-multiple-versions-of-visual-studio.md)você pode ler sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] as vantagens e problemas de suporte a instalações lado a lado de instalações compartilhadas ou lado a lado do seu VSPackage. Em suma, os VSPackages lado a lado dão-lhe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a maior flexibilidade para suportar novos recursos de .

Os cenários discutidos neste tópico não são suas únicas escolhas, mas são apresentados como práticas recomendadas sugeridas.

## <a name="components-privacy-and-sharing"></a>Componentes, Privacidade e Compartilhamento

### <a name="make-your-components-independent"></a>Torne seus componentes independentes

Depois de identificar e preencher um `GUID`componente, atribuir um e implantar o componente, você não poderá alterar sua composição. Se você alterar a composição de um componente, o componente resultante `GUID`deve ser um novo componente com um novo . Diante desses fatos, a maior flexibilidade de versão é proporcionada por tornar cada componente independente, unidade auto-confiante. Para obter mais informações sobre as regras que regem os componentes, consulte [Alterando o Código dos Componentes](/windows/desktop/Msi/changing-the-component-code) e [o que acontece se as regras dos componentes forem quebradas?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Não misture recursos compartilhados e privados em um componente

A contagem de referência socorre no nível do componente. Consequentemente, a mistura de recursos compartilhados e privados em um componente torna impossível atualizar recursos privados, como um arquivo executável, sem também substituir recursos compartilhados. Esse cenário cria problemas de retrocompatibilidade e o restringe de criar capacidade lado a lado.

Por exemplo, os valores de registro [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] usados para registrar seu VSPackage com o deve ser mantido em um componente separado daquele usado para registrar seu VSPackage com o Visual Studio. Arquivos compartilhados ou valores de registro vão em outro componente.

## <a name="scenario-1-shared-vspackage"></a>Cenário 1: VSPackage compartilhado

Neste cenário, um VSPackage compartilhado (um único binário que suporta várias versões do Visual Studio é enviado em um pacote do Windows Installer. O registro com cada versão do Visual Studio é controlado por recursos selecionáveis pelo usuário. Isso também significa que, quando atribuído a recursos separados, cada componente pode ser selecionado individualmente para instalação ou [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]desinstalação, colocando o usuário no controle de integrar o VSPackage em diferentes versões de . (Consulte [os recursos do Instalador do Windows](/windows/desktop/Msi/windows-installer-features) para obter mais informações sobre o uso de recursos em pacotes do Windows Installer.)

![Vs compartilhado svspackage instalador](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Como mostrado na ilustração, os componentes compartilhados são feitos parte do recurso Feat_Common, que está sempre instalado. Ao tornar visíveis os recursos de Feat_VS2002 e Feat_VS2003, os usuários podem escolher na hora de instalar em quais versões do Visual Studio querem que o VSPackage se integre. Os usuários também podem usar o modo de manutenção do Windows Installer para adicionar ou remover recursos, que neste caso adiciona ou remove as informações de registro do VSPackage de diferentes versões do Visual Studio.

> [!NOTE]
> Definir a coluna Exibir de um recurso como 0 a esconde. Um valor de coluna de baixo nível, como 1, garante que ele será sempre instalado. Para obter mais informações, consulte [INSTALLLEVEL Property](/windows/desktop/Msi/installlevel) e [Feature Table](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Cenário 2: Atualização compartilhada do VSPackage

Neste cenário, uma versão atualizada do instalador VSPackage no cenário 1 é enviada. Para fins de discussão, a atualização adiciona suporte ao Visual Studio, mas também pode ser um patch de segurança mais simples ou um pacote de serviço de correção de bugs. As regras do Windows Installer para instalar componentes mais novos exigem que os componentes inalterados já existentes no sistema não sejam recopiados. Neste caso, um sistema com a versão 1.0 já presente substituirá o componente atualizado Comp_MyVSPackage.dll e permitirá que os usuários optem por adicionar o novo recurso Feat_VS2005 com seu componente Comp_VS2005_Reg.

> [!CAUTION]
> Sempre que um VSPackage é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]compartilhado entre várias versões de , é essencial que as versões subseqüentes do VSPackage mantenham a compatibilidade retrógrada com versões anteriores do Visual Studio. Onde você não pode manter a compatibilidade retrógrada, você deve usar VSPackages privados lado a lado. Para obter mais informações, consulte [Suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalador de atualização de pacote VS compartilhado vs](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

Este cenário apresenta um novo instalador DE VSPackage, aproveitando o suporte do Windows Installer para pequenas atualizações. Os usuários simplesmente instalam a versão 1.1 e ele atualiza a versão 1.0. No entanto, não é necessário ter a versão 1.0 no sistema. O mesmo instalador instalará a versão 1.1 em um sistema sem a versão 1.0. A vantagem de fornecer pequenos upgrades desta forma é que não é necessário passar pelo trabalho de desenvolver um instalador de upgrade e um instalador de produto completo. Um instalador faz os dois trabalhos. Uma correção de segurança ou um pacote de serviço podem, em vez disso, tirar proveito dos patches do Instalador do Windows. Para obter mais informações, consulte [Patches e Upgrades](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Cenário 3: Pacote VS lado a lado

Este cenário apresenta dois instaladores VSPackage — um para cada versão do Visual Studio .NET 2003 e visual studio. Cada instalador instala um VSPackage lado a lado, ou privado ( um que é especificamente construído e instalado para uma versão específica do Visual Studio). Cada VSPackage está em seu próprio componente. Consequentemente, cada um pode ser reparado individualmente com patches ou liberações de manutenção. Como o VSPackage DLL agora é específico da versão, é seguro incluir suas informações de registro no mesmo componente da DLL.

![Vs Side-by-Side VS Instalador de pacotes](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Cada instalador também inclui código que é compartilhado entre os dois instaladores. Se o código compartilhado estiver instalado em um local comum, a instalação de ambos os arquivos .msi instalará o código compartilhado apenas uma vez. O segundo instalador apenas incrementa uma contagem de referência no componente. A contagem de referência garante que, se um dos VSPackages for desinstalado, o código compartilhado permanecerá para o outro VSPackage. Se o segundo VSPackage também estiver desinstalado, o código compartilhado será removido.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Cenário 4: Atualização de vspackage lado a lado

Neste cenário, o vsPackage for Visual Studio sofreu uma vulnerabilidade de segurança e você precisa emitir uma atualização. Como no cenário 2, você pode criar um novo arquivo .msi que atualiza uma instalação existente para incluir a correção de segurança, bem como implantar novas instalações com a correção de segurança já existente.

Neste caso, o VSPackage é um VSPackage gerenciado instalado no cache de montagem global (GAC). Ao reconstruí-lo para incluir a correção de segurança, você deve alterar a parte do número de revisão do número da versão de montagem. As informações de registro do novo número da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versão de montagem substituem a versão anterior, fazendo com que carregue o conjunto fixo.

![Vs Side-by-Side VS Package Update installer](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Para obter mais informações sobre a implantação de conjuntos lado a lado, consulte [Simplificando a implantação e a resolução do inferno DLL com o .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Confira também

- [Instalador do Windows](/windows/desktop/Msi/windows-installer-portal)
- [Fornecer suporte à várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
