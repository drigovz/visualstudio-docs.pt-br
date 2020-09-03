---
title: Preparar para depurar projetos C++ | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: dc663115e98d7553e03a186874d59b75eb68cb90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916316"
---
# <a name="debugging-preparation-c-project-types"></a>Preparação da depuração: tipos de projeto C++
Esta seção descreve como depurar os tipos de projeto básicos criados pelos modelos de projeto do [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].

 Observe que os tipos de projeto que criam DLLs como sua saída foram agrupados na [depuração de projetos DLL](../debugger/debugging-dll-projects.md) devido aos recursos comuns que eles compartilham.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Neste tópico
 [Configurações de propriedade recomendadas](#BKMK_Recommended_Property_Settings)

 [Projetos Win32](#BKMK_Win32_Projects)

- [Para depurar um aplicativo Win32 C ou C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Para definir manualmente uma configuração de depuração](#BKMK_To_manually_set_a_Debug_configuration)

  [Aplicativos do Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Configurações de propriedade recomendadas
 Certas propriedades devem ser definidas da mesma maneira para todos os cenários não gerenciados de depuração. As tabelas a seguir exibem as configurações de propriedade recomendadas. As configurações não listadas aqui podem variar entre os tipos de projeto não gerenciados diferentes. Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propriedades de configuração &#124; C/C++ &#124; nó de otimização

|Nome da propriedade|Configuração|
|-------------------|-------------|
|**Otimização**|Definido como **Desabilitado (/0d).** O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, habilite essa configuração, mas lembre-se de que o código mostrado na janela **Desmontagem** é gerado da origem otimizada que pode não corresponder ao que é visto em suas janelas de origem. Outros recursos, como depuração, podem não se comportar como esperado.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propriedades de configuração &#124; vinculador &#124; nó de depuração

|Nome da propriedade|Configuração|
|-------------------|-------------|
|**Gerar informações de depuração**|Você sempre deve definir essa opção como **Sim (/DEBUG)** para criar os símbolos e os arquivos de depuração necessários para a depuração. Quando o aplicativo entra em produção, você pode defini-lo como desativado.|

 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Projetos Win32
 Os aplicativos Win32 são programas do Windows tradicionais escritos em C ou C++. Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simples.

 Os aplicativos Win32 incluem aplicativos do MFC e projetos do ATL. Eles usam APIs do Windows e podem usar MFC ou ATL, mas não usam Common Language Runtime (CLR). Podem, no entanto, chamar código gerenciado que usa o CLR.

 O procedimento a seguir explica como depurar um projeto do Win32 de dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Outro modo de depurar um aplicativo Win32 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Para depurar um aplicativo Win32 C ou C++

1. Abra o projeto no Visual Studio.

2. No menu **depurar** , escolha **Iniciar**.

3. Depure usando as técnicas discutidas na [primeira olhada no depurador](../debugger/debugger-feature-tour.md).

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Para definir manualmente uma configuração de depuração

1. No menu **Exibir**, clique em **Página de Propriedades**.

2. Clique no nó **Propriedades de Configuração** para abri-lo se ele não ainda estiver aberto

3. Selecione **Geral** e defina o valor da linha **Saída** para **Depurar**.

4. Abra o nó **C/C++** e selecione **Geral**.

    Na linha **Depurar**, especifique o tipo de informações de depuração a ser geradas pelo compilador. Você pode escolher valores como **Banco de dados do programa (/Zi)** ou **Banco de dados do programa para edição e continuação (/ZI)**.

5. Selecione **Otimização** e, na linha **Otimização**, selecione **Desabilitado (/0d)** na lista suspensa.

    O código otimizado é mais difícil de depurar porque as instruções geradas não correspondem diretamente ao código-fonte. Se você descobrir que seu programa tem um bug que aparece apenas em código otimizado, poderá ativar essa configuração, mas lembre-se de que o código mostrado na janela Desmontagem é gerado de origem otimizada que pode não corresponder ao que é visto em suas janelas de origem. Os recursos como o depuração provavelmente mostram incorretamente pontos de interrupção e ponto de execução.

6. Abra o nó **Vinculador** e selecione **Depuração**. Na primeira linha **Gerar**, selecione **Sim (/DEBUG)** na lista suspensa. Sempre defina isso quando você estiver depurando.

   Para obter mais informações, consulte[configurações de projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="windows-forms-applications-net"></a><a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms aplicativos (.NET)
 O modelo **Aplicativo do Windows Forms (.NET)** cria um aplicativo do Windows Forms do [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é semelhante a depurar em aplicativos gerenciados do Windows Forms.

 Quando você cria um projeto do Windows Forms com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de depuração e versão. Se necessário, você pode alterar essas configurações na caixa de diálogo ** \<project name> páginas de propriedades** . Para obter mais informações, confira [Configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).

 Para obter mais informações, consulte [configurações de projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Outro modo de depurar um aplicativo do Windows Forms 2 é iniciar o aplicativo fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e anexar a ele. Para obter mais informações, confira [Anexando a um programa ou a vários programas em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [Neste tópico](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Confira também
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
- [Definições do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Anexando a um programa ou a vários programas em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)
- [Como Criar um Projeto de Aplicativo do Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))