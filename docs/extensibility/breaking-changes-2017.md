---
title: Quebrando mudanças na extensibilidade do Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739975"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Mudanças na extensibilidade do Visual Studio 2017

O Visual Studio 2017 oferece uma [experiência de instalação visual studio mais rápida e leve](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) que reduz o impacto do Visual Studio nos sistemas de usuários, ao mesmo tempo em que dá aos usuários uma maior escolha sobre as cargas de trabalho e recursos que estão instalados. Para apoiar essas melhorias, fizemos mudanças no modelo de extensibilidade, incluindo algumas mudanças de ruptura. Este artigo descreve os detalhes técnicos dessas mudanças e o que pode ser feito para enfrentá-las.

> [!NOTE]
> Algumas informações são detalhes de implementação point-in-time e podem ser alteradas posteriormente.

## <a name="changes-affecting-vsix-format-and-installation"></a>Mudanças que afetam o formato e a instalação do VSIX

O Visual Studio 2017 introduziu o formato VSIX v3 (versão 3) para suportar a experiência de instalação leve.

As alterações no formato VSIX incluem:

* Declaração de pré-requisitos de configuração. Para cumprir a promessa de um Visual Studio leve e rápido, o instalador agora oferece mais opções de configuração aos usuários. Como resultado, para garantir que os recursos e componentes exigidos por uma extensão sejam instalados, as extensões precisam declarar suas dependências.

  * O instalador Visual Studio 2017 oferece automaticamente a aquisição e instalação dos componentes necessários para o usuário como parte da instalação de sua extensão.
  * Os usuários também são avisados ao tentar instalar uma extensão que não foi construída usando o novo formato VSIX v3, mesmo que tenham sido marcados em seu manifesto como alvo da versão 15.0.

* Recursos aprimorados para o formato VSIX. Para fornecer uma [instalação de baixo impacto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) do Visual Studio que também suporta instalações lado a lado, não salvamos mais a maioria dos dados de configuração no registro do sistema e mudamos os conjuntos específicos do Visual Studio para fora do GAC. Também aumentamos as capacidades do formato VSIX e do mecanismo de instalação VSIX, permitindo que você o use em vez de um MSI ou EXE para instalar suas extensões para alguns tipos de instalação.

Os novos recursos incluem:

* Registro na instância especificada do Visual Studio.
* Instalação fora da [pasta de extensões](set-install-root.md).
* Detecção de arquitetura de processador.
* Dependência de pacotes de idiomas separados por idiomas.
* Instalação com [suporte ngen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Construa uma extensão para o Visual Studio 2017

As ferramentas de designer para a autoria do novo formato vSIX v3 manifesto estão disponíveis no Visual Studio 2017. Veja o documento que acompanha [Como: Migrar projetos de extensibilidade para o Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) para obter detalhes sobre o uso das ferramentas de designer ou fazer atualizações manuais para o projeto e se manifestar para desenvolver extensões VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Mudança: Caminho de dados do usuário do Visual Studio

Anteriormente, apenas uma instalação de cada grande lançamento do Visual Studio poderia existir em cada máquina. Para suportar instalações lado a lado do Visual Studio 2017, vários caminhos de dados do usuário para o Visual Studio podem existir na máquina do usuário.

O código que é executado dentro do processo do Visual Studio deve ser atualizado para usar o Visual Studio Settings Manager. O código executado fora do processo do Visual Studio pode encontrar o caminho do usuário de uma instalação específica do Visual Studio [seguindo a orientação aqui](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Mudança: Cache de montagem global (GAC)

A maioria dos conjuntos de núcleos do Visual Studio não estão mais instalados no GAC. As seguintes alterações foram feitas para que o código executado no processo do Visual Studio ainda possa encontrar montagens necessárias em tempo de execução.

> [!NOTE]
> [INSTALLDIR] abaixo refere-se ao diretório raiz de instalação do Visual Studio. *O VSIXInstaller.exe* preencherá isso automaticamente, mas para escrever código de implantação personalizado, leia [a localização do Visual Studio](locating-visual-studio.md).

* Assembléias que foram instaladas apenas no GAC:

  Esses conjuntos estão agora instalados em <em>\*[INSTALLDIR]\Common7\IDE , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR]\Common7\IDE\PrivateAssemblies*. Essas pastas fazem parte dos caminhos de sondagem do processo do Visual Studio.

* Conjuntos que foram instalados em um caminho de não sondagem e no GAC:

  * A cópia no GAC foi removida da configuração.
  * Um arquivo *.pkgdef* foi adicionado para especificar uma entrada base de código para o conjunto.

    Por exemplo:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Em tempo de execução, o subsistema Visual Studio pkgdef mescla essas entradas no arquivo de configuração em tempo de execução do processo Visual Studio (em *[VSAPPDATA]\devenv.exe.config*) como [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementos. Esta é a maneira recomendada de deixar o processo do Visual Studio encontrar sua montagem, pois evita pesquisar através de caminhos de sondagem.

### <a name="reacting-to-this-breaking-change"></a>Reagindo a essa mudança de ruptura

* Se sua extensão estiver sendo executado dentro do processo do Visual Studio:

  * Seu código será capaz de encontrar conjuntos de núcleos do Visual Studio.
  * Considere usar um arquivo *.pkgdef* para especificar um caminho para seus conjuntos, se necessário.

* Se sua extensão estiver sendo executado fora do processo do Visual Studio:

  Considere procurar conjuntos de núcleos do Visual Studio em <em>\*[INSTALLDIR]\Common7\IDE , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> ou *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* usando arquivo de configuração ou resolver o conjunto.

## <a name="change-reduce-registry-impact"></a>Mudança: Reduzir o impacto do registro

### <a name="global-com-registration"></a>Registro global de COM

* Anteriormente, o Visual Studio instalou muitas chaves de registro no HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE colmeias para suportar o registro com nativo. Para eliminar esse impacto, o Visual Studio agora usa [ativação sem registro para componentes COM](https://msdn.microsoft.com/library/ms973913.aspx).
* Como resultado, a maioria dos arquivos TLB / OLB / DLL em %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv não são mais instalados por padrão pelo Visual Studio. Esses arquivos estão agora instalados em [INSTALLDIR] com os correspondentes manifestos COM sem registro usados pelo processo de host do Visual Studio.
* Como resultado, o código externo que depende do registro global com para interfaces Visual Studio COM não encontrará mais esses registros. O código que está sendo executado dentro do processo do Visual Studio não verá diferença.

### <a name="visual-studio-registry"></a>Registro do Visual Studio

* Anteriormente, o Visual Studio instalou muitas chaves de registro nas **colmeias de HKEY_LOCAL_MACHINE** e **HKEY_CURRENT_USER** do sistema sob uma chave específica do Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio\{Versão}**: Chaves de registro criadas por instaladores MSI e extensões por máquina.
  * **HKCU\Software\Microsoft\VisualStudio\{Versão}**: Chaves de registro criadas pelo Visual Studio para armazenar configurações específicas do usuário.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Uma cópia da chave Visual Studio HKLM acima, além das chaves de registro mescladas a partir de arquivos *.pkgdef* por extensões.

* Para reduzir o impacto no registro, o Visual Studio agora usa a função [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) para armazenar chaves de registro em um arquivo binário privado em *[VSAPPDATA]\privateregistry.bin*. Apenas um número muito pequeno de chaves específicas do Visual Studio permanecem no registro do sistema.
* O código existente que está sendo executado dentro do processo do Visual Studio não é afetado. O Visual Studio redirecionará todas as operações de registro sob a chave específica do HKCU Visual Studio para o registro privado. A leitura e a escrita em outros locais de registro continuarão a usar o registro do sistema.
* O código externo precisará carregar e ler a partir deste arquivo para entradas de registro do Visual Studio.

### <a name="react-to-this-breaking-change"></a>Reaja a essa mudança de ruptura

* O código externo deve ser convertido para usar a ativação Sem registro para componentes COM também.
* Os componentes externos podem encontrar a localização do Visual Studio [seguindo a orientação aqui](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Recomendamos que os componentes externos usem o Gerenciador de [Configurações Externas](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) em vez de ler/escrever diretamente nas teclas de registro do Visual Studio.
* Verifique se os componentes que sua extensão está usando podem ter implementado outra técnica para registro. Por exemplo, as extensões de depurador podem ser capazes de aproveitar o novo [registro COM do arquivo JSON msvsmon](migrate-debugger-COM-registration.md).
