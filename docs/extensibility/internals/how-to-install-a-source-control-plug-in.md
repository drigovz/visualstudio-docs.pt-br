---
title: 'Como: Instalar um Plug-in de controle de origem | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707989"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Como: Instalar um plug-in de controle de origem
A criação de um plug-in de controle de origem envolve três etapas:

1. Crie uma DLL com as funções definidas na seção de referência da API plug-in de controle de fonte desta documentação.

2. Implemente as funções definidas pela API do Controle de Origem. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] for chamada, disponibilize interfaces e caixas de diálogo no plug-in.

3. Registre o DLL fazendo entradas de registro apropriadas.

## <a name="integration-with-visual-studio"></a>Integração com o Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]suporta plug-ins de controle de origem que estejam em conformidade com a API plug-in de controle de origem.

### <a name="register-the-source-control-plug-in"></a>Registre o plug-in de controle de origem
 Antes que um ambiente de desenvolvimento integrado em execução (IDE) possa chamar para o sistema de controle de origem, ele deve primeiro encontrar o DLL plug-in de controle de origem que exporta a API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar o dll plug-in de controle de origem

1. Adicione duas entradas na tecla **HKEY_LOCAL_MACHINE** na subchave **SOFTWARE** que especifica a subchave do nome da empresa, seguida pela subchave do nome do produto. O padrão é **\\\<HKEY_LOCAL_MACHINE\SOFTWARE \\ \<nome \\ \<da empresa>nome do produto>** *valor*de entrada> = . As duas entradas são sempre chamadas **sCCServerName** e **SCCServerPath**. Cada uma é uma corda normal.

    Por exemplo, se o nome da empresa for Microsoft e seu produto de controle de origem for chamado SourceSafe, esse caminho de registro será **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. Nesta subchave, a primeira entrada, **SCCServerName,** é uma string legível pelo usuário nomeando seu produto. A segunda entrada, **SCCServerPath,** é o caminho completo para o DLL de controle de origem ao que o IDE deve conectar. O seguinte fornece entradas de registro de amostra:

   |Entrada do Registro de Amostras|Valor de exemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath é o caminho completo para o plug-in SourceSafe. Seu plug-in de controle de origem usará diferentes nomes de empresas e produtos, mas os mesmos caminhos de entrada de registro.

2. As seguintes entradas de registro opcionais podem ser usadas para modificar o comportamento do plug-in de controle de origem. Essas entradas vão na mesma subchave que **SccServerName** e **SccServerPath**.

   - A entrada **HideInVisualStudioregistry** pode ser usada se você não quiser que seu plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de controle de origem apareça na lista De seleção de **plug-in** de . Esta entrada também afetará a comutação automática para o plug-in de controle de origem. Um possível uso para esta entrada é se você fornecer um pacote de controle de origem que substitui o plug-in de controle de origem, mas você deseja tornar mais fácil para o usuário migrar do uso do plug-in de controle de origem para o pacote de controle de origem. Quando o pacote de controle de origem é instalado, ele define esta entrada de registro, que oculta o plug-in.

      **HideInVisualStudio** é um valor DWORD e está definido como *1* para ocultar o plug-in ou *0* para mostrar o plug-in. Se a entrada do registro não aparecer, o comportamento padrão é mostrar o plug-in.

   - A entrada de registro **DisableSccManager** pode ser usada para desativar ou ocultar a opção de menu de menu **de>do Servidor de Controle de Origem de Origem de Lançamento \<** que normalmente aparece no submenu Controle de origem**de** **arquivo.** >  A seleção desta opção de menu chama a função [SccRunScc.](../../extensibility/sccrunscc-function.md) Seu plug-in de controle de origem pode não suportar um programa externo e, portanto, você pode querer desativar ou até mesmo ocultar a opção **De** iniciar menu.

      **DesabiliteSccManager** é um valor DWORD e está definido como *0* para habilitar a opção de menu **de menu do Servidor de Controle de Fonte de Lançamento \<>,** definida como *1* para desativar a opção de menu e definida como *2* para ocultar a opção de menu. Se esta entrada de registro não aparecer, o comportamento padrão será mostrar a opção menu.

   | Entrada de registro de amostra | Valor de exemplo |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideinVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Adicione a subchave, **SourceCodeControlProvider**, sob a **chave HKEY_LOCAL_MACHINE** na subchave **SOFTWARE.**

    Sob esta subchave, o Provedor de entrada **de registroRegKey** é definido como uma string que representa a subchave que você colocou no registro na etapa 1. O padrão é **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *SOFTWARE\\<nome\> \\ da empresa<nome\>do produto*.

    A seguir está o conteúdo da amostra desta subchave.

   |Entrada de Registro|Valor de exemplo|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Seu plug-in de controle de origem usará a mesma subchave e nomes de entrada, mas o valor será diferente.

4. Crie uma subchave chamada **InstalledSCCProviders** sob a sub-chave **SourceCodeControlProvider** e, em seguida, coloque uma entrada sob essa subchave.

    O nome desta entrada é o nome legível pelo usuário do provedor (o mesmo que o valor especificado para a entrada SCCServerName), e o valor é, mais uma vez, a subchave criada na etapa 1. O padrão é **\\ HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\><nome** = de exibição*SOFTWARE\\<nome\> \\ da empresa<nome\>do produto*.

    Por exemplo:

   |Entrada de registro de amostra|Valor de exemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Pode haver vários plug-ins de controle de origem registrados desta forma. É assim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que se encontra todos os plug-ins instalados baseados em API de controle de fonte.

## <a name="how-an-ide-locates-the-dll"></a>Como um IDE localiza o DLL
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tem duas maneiras de encontrar o DLL plug-in de controle de origem:

- Encontre o plug-in padrão do controle de origem e conecte-se a ele silenciosamente.

- Encontre todos os plug-ins de controle de origem registrados, dos quais o usuário escolhe um.

  Para localizar a DLL de primeira forma, o IDE procura sob a **subchave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** para o **provedor de entradaRegKey**. O valor desta entrada aponta para outra subchave. Em seguida, o IDE procura uma entrada chamada **SccServerPath** nessa segunda subchave sob **HKEY_LOCAL_MACHINE**. O valor desta entrada aponta o IDE para o DLL.

> [!NOTE]
> O IDE não carrega DLLs de caminhos relativos (por exemplo, *.\NewProvider.DLL*). Um caminho completo para a DLL deve ser especificado (por exemplo, *c:\Providers\NewProvider.DLL*). Isso reforça a segurança do IDE, impedindo o carregamento de DLLs plug-in não autorizados ou personificados.

 Para localizar a DLL de segunda forma, o IDE analisa a **subchave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** para todas as entradas. Cada entrada tem um nome e um valor. O IDE exibe uma lista desses nomes para o usuário. Quando o usuário escolhe um nome, o IDE encontra o valor para o nome selecionado que aponta para uma subchave. O IDE procura uma entrada chamada **SccServerPath** nessa subchave em **HKEY_LOCAL_MACHINE**. O valor dessa entrada aponta o IDE para a DLL correta.

 Um plug-in de controle de origem precisa suportar ambas as formas de encontrar a DLL e, consequentemente, define **ProviderRegKey**, substituindo qualquer configuração anterior. Mais importante, ele deve adicionar-se à lista de **Provedores instalados** para que o usuário possa ter uma escolha de qual plug-in de controle de origem usar.

> [!NOTE]
> Como a chave **HKEY_LOCAL_MACHINE** é usada, apenas um plug-in de controle de origem pode ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrado como o plug-in padrão de controle de origem em uma determinada máquina (no entanto, permite que os usuários determinem qual plug-in de controle de origem eles querem realmente usar para uma determinada solução). Durante o processo de instalação, verifique se um plug-in de controle de origem já está definido; se assim for, pergunte ao usuário se deve ou não definir o novo plug-in de controle de origem sendo instalado como padrão. Durante a desinstalação, não remova outras subchaves de registro comuns a todos os plug-ins de controle de origem em **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; remover apenas a sua subchave SCC particular.

## <a name="how-the-ide-detects-version-1213-support"></a>Como o IDE detecta o suporte à versão 1.2/1.3
 Como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detecta se um plug-in suporta a funcionalidade 1.2 e 1.3 do Source Control Plug-in? Para declarar capacidade avançada, o plug-in de controle de origem deve implementar a função correspondente:

 Primeiro, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verifica o valor devolvido ligando para o [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve ser maior ou igual a 1,2.

 Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguida, determina se o novo recurso em `lpSccCaps` particular é suportado examinando o argumento no [SccInitialize](../../extensibility/sccinitialize-function.md).

 Se ambas as condições forem atendidas, as novas funções suportadas nas versões 1.2 e 1.3 podem ser chamadas.

## <a name="see-also"></a>Confira também
- [Comece com plug-ins de controle de origem](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
