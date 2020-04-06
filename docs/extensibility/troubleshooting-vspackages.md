---
title: Solução de problemas VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698923"
---
# <a name="troubleshooting-vspackages"></a>Solucionando problemas de VSPackages
A seguir estão problemas comuns que você pode ter com o seu VSPackage e dicas para resolver os problemas.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Para solucionar problemas de um VSPackage que impede o Visual Studio de começar

- Comece [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em modo de segurança.

   Para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] iniciar no modo de segurança, em um prompt de comando, **digite devenv.exe /safemode**.

   Durante este processo, nenhum VSPackages é carregado, exceto os VSPackages incluídos com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Para solucionar problemas de um VSPackage que não carrega

1. Certifique-se de que você está usando a raiz de registro na qual o VSPackage está registrado para ser executado, geralmente a raiz do registro experimental.

    Para obter mais informações, consulte [A Instância Experimental](../extensibility/the-experimental-instance.md).

2. Se o VSPackage for direcionado para ser executado na raiz do registro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]experimental, certifique-se de que você está executando a versão experimental de .

    Para executar a versão experimental, digite o seguinte em uma janela de comando: **devenv /rootsuffix exp**.

3. Verifique suas entradas de registro de vsPackage.

    Para obter mais informações, consulte [Registrando VSPackages](registering-and-unregistering-vspackages.md) e [gerenciando VSPackages](../extensibility/managing-vspackages.md).

4. Abra a janela **Saída** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da instância disso não está conseguindo carregar o VSPackage. Informações sobre por que o VSPackage está falhando em carregar podem ser exibidas nessa janela.

   > [!NOTE]
   > Se você estiver iniciando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versão experimental do ambiente de desenvolvimento integrado (IDE), inspecione a janela **Saída** de ambas as versões.

5. Examine o registro de atividades.

    Para obter mais informações, [consulte Como: Usar o Registro de Atividades](../extensibility/how-to-use-the-activity-log.md).

6. Para obter mais informações sobre exceções lançadas pelo IDE, clique em **Exceções** no menu **Depuração** para ativar as exceções. Na caixa de diálogo **Exceções,** selecione os tipos de exceções sobre as quais você deseja mais informações.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Para solucionar problemas de um VSPackage que não registra

1. Certifique-se de que o conjunto VSPackage resida em um local confiável. O RegPkg não pode registrar conjuntos em um local não confiável ou parcialmente confiável, como um compartilhamento de rede na configuração de segurança padrão .net. Embora um aviso apareça sempre que um usuário cria um projeto em um local não confiável, a caixa de seleção "não mostre esta mensagem novamente" pode impedir que esse aviso ocorra novamente.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Para solucionar problemas de um comando que não é visível ou que gera um erro quando você clica em um comando

1. Mesclar os comandos de menu novo ou alterado e os [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que já estão no IDE digitando o seguinte no Prompt de comando: **devenv /rootsufix Exp /setup**.

2. Certifique-se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de que pode encontrar UI.dll para o seu VSPackage.

   1. Encontre o CLSID do VSPackage na seção Pacotes do registro:

        HKLM\Software\Microsoft\Visual\\Studio*\<versão>* \Pacotes

   2. Verifique se o caminho dado pela subchave SatelliteDll está correto.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Para solucionar problemas de um VSPackage que se comporta inesperadamente

1. Defina os pontos de interrupção no seu código.

     Bons pontos de partida para depuração são o construtor e o método de inicialização. Você também pode definir pontos de interrupção na área que deseja avaliar, como um comando de menu. Para habilitar pontos de interrupção, você deve ser executado sob o depurador.

    1. No menu **Projeto** , clique em **Propriedades**.

    2. Na caixa de diálogo **Páginas** de propriedade, selecione a guia **Depuração.**

    3. Na caixa **de argumentos da linha de comando,** digite o sufixo raiz do ambiente de desenvolvimento que seu VSPackage tem como alvo. Por exemplo, para selecionar a compilação experimental, digite: **/RootSuffix Exp**.

    4. No menu **Debug,** clique em **Iniciar depuração** ou pressione F5.

        > [!NOTE]
        > Se você estiver depurando um projeto, crie ou carregue uma instância existente do seu projeto agora.

2. Use o registro de atividades.

     Rastreie o comportamento do VSPackage escrevendo informações no registro de atividades em pontos-chave. Esta técnica é especialmente útil quando você executa um VSPackage em um ambiente de varejo. Para obter mais informações, [consulte Como: Usar o Registro de Atividades](../extensibility/how-to-use-the-activity-log.md).

3. Use símbolos públicos.

     Para melhorar a legibilidade durante a depuração, você pode anexar símbolos ao depurador.

    1. No menu **Ferramentas/Opções,** navegue até a caixa de diálogo **Depuração/Símbolos.**

    2. Adicionar este **local do arquivo Símbolo (.pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Para melhorar o desempenho, especifique uma pasta de cache de símbolo, por exemplo:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Para solucionar problemas de um VSPackage ausente ou uma de suas dependências

1. Para código gerenciado, certifique-se de que os caminhos de referência estão corretos.

   1. No menu **Projeto** , clique em **Propriedades**.

   2. Selecione a guia **Referências** na caixa de diálogo **Páginas** de propriedade e certifique-se de que todos os caminhos estão corretos. Alternativamente, você pode usar o **Navegador de Objetos** para procurar os objetos referenciados.

        Para código gerenciado, você pode usar o [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) para exibir os detalhes das cargas de montagem com falha.

2. Para obter código não gerenciado, encontre o CLSID do VSPackage no nó de registro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID:

    HKLM\Software\Microsoft\Visual\\Studio*\<versão>* \CLSID

   Certifique-se de que a entrada InprocServer32 tenha o caminho correto da dll VSPackage.

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
