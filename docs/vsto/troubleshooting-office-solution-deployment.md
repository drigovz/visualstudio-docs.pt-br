---
title: Implantação de solução do Office para solução de solução de solução de solução de solução de solução
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444928"
---
# <a name="troubleshoot-office-solution-deployment"></a>Implantação de solução do Office para solução de solução de solução de solução de solução de solução
  Este tópico contém informações sobre como resolver problemas comuns que você pode encontrar quando implantar soluções do Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Solucionar problemas das soluções do Office usando o visualizador de eventos
 Você pode usar o visualizador de eventos no Windows [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para ver mensagens de erro capturadas pela instalação ou desinstalação de soluções do Office. Você pode usar essas mensagens do registrador de eventos para resolver problemas de instalação e implantação. Para obter mais informações, consulte [registro de eventos para soluções do Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Alterar o nome da montagem causa conflitos
 Se você alterar o valor **do nome de montagem** na página de **aplicativo** do **Project Designer** depois de já ter implantado uma solução, as ferramentas de publicação modificarão o pacote de configuração para ter um arquivo *Setup.exe* e dois manifestos de implantação. Se você implantar dois arquivos manifestos, as seguintes condições podem ocorrer:

- Se o usuário final instalar ambas as versões, o aplicativo carregará ambos os Complementos VSTO.

- Se o Add-in VSTO foi instalado antes do nome do conjunto ser alterado, o usuário final nunca receberá atualizações.

  Para evitar essas condições, não altere o valor do nome de **montagem** da solução depois de implantar a solução.

## <a name="check-for-updates-takes-a-long-time"></a>Verificar se as atualizações levam muito tempo
 Visual Studio 2010 Tools for Office runtime fornece uma entrada de registro que os administradores podem usar para definir o valor de tempo para baixar os manifestos e a solução.

#### <a name="to-set-the-time-out-value"></a>Para definir o valor de tempo de saída

1. No registro, navegue até a seguinte tecla:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. Na sub-tecla **AddInTimeout,** defina o valor de tempo em milissegundos.

     Se a subchave **AddInTimeout** não existir, crie-a como um DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Não é possível atualizar ou publicar para um compartilhamento de arquivos de rede
 As soluções do Office que estão em um compartilhamento de arquivos de rede podem exibir uma mensagem enganosa durante as atualizações se o arquivo *Setup.exe* da solução estiver bloqueado em um processo enquanto a atualização está sendo publicada. A mensagem pode dizer o seguinte: "Incapaz de adicionar 'setup.exe' à Web. O arquivo 'setup.exe' já existe nesta Web."

 Para ajudar a evitar o bloqueio de arquivos, você pode fazer o compartilhamento somente leitura para os usuários finais. No entanto, se os documentos estiverem no compartilhamento, eles também se tornarão somente leitura para os usuários finais.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Pré-requisitos para o Microsoft Office não estão instalados
 Você pode adicionar as assembléias de interop .NET, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]e o Office primary interop ao seu pacote de configuração como pré-requisitos que são implantados com a solução do Office. Para obter informações sobre como instalar os conjuntos de interop primários, consulte [Configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) e [como: Instalar conjuntos de interop primários do Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Publicar usando o Localhost pode causar problemas de instalação
 Quando você `http://localhost` usa como local de publicação ou instalação para soluções de nível de documento, o **Assistente de publicação** não converte a seqüência para o nome real do computador. Neste caso, a solução deve ser instalada no computador de desenvolvimento. Para fazer com que as soluções implantadas usem o IIS no computador de desenvolvimento, use o nome totalmente qualificado para todos os locais HTTP/HTTPS/FTP em vez de host local.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Os conjuntos armazenados em cache são carregados em vez de conjuntos atualizados
 Fusion, o carregador de montagem .NET Framework, carrega a cópia armazenada em cache dos conjuntos quando o caminho de saída do projeto está em um compartilhamento de arquivos de rede, o conjunto é assinado com um nome forte e a versão de montagem da personalização não muda. Se você atualizar um conjunto que atenda a essas condições, a atualização não aparecerá na próxima vez que você executar o projeto porque a cópia em cache está carregada.

 Você pode configurar o Visual Studio para que o Fusion baixe montagens toda vez que o projeto for executado.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Para baixar conjuntos em vez de carregar cópias em cache

1. Na barra de menus, escolha **Project**, _ProjectName_**Properties**.

2. Na página **Aplicativo,** escolha **Informações de montagem**.

3. Defina o número de revisão, terceiro campo, da\*Versão de **Montagem,** como um curinga ( ). Por exemplo, "1.0.*".  Em seguida, escolha o botão **OK.**

   Depois de alterar a versão de montagem, você pode continuar a assinar seu conjunto com um nome forte, e o Fusion carregará a versão mais recente da personalização.

 [!NOTE]
> Começando com o Visual Studio 2017, se você tentar usar wild cards na Versão de montagem, um erro de compilação ocorrerá.  Isso porque os wild cards na versão de montagem quebrarão o recurso Determinístico MSBuild. Você será instruído a remover os curingas da versão de montagem ou desativar o determinismo.  Para saber mais sobre o recurso Determinístico, consulte: Propriedades comuns do [projeto MSBuild](../msbuild/common-msbuild-project-properties.md) e [Personalize sua compilação](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>A instalação falha quando o URI tem caracteres que não são US-ASCII
 Quando você publica uma solução do Office para um local HTTP/HTTPS/FTP, o caminho não pode ter nenhum caractere Unicode que não esteja nos EUA-ASCII. Tais caracteres podem causar comportamento inconsistente no programa Configuração. Use caracteres US-ASCII para o caminho de instalação.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Solicitar a desinstalação manual do aparece quando você publica e instala uma solução no computador de desenvolvimento
 Quando você constrói uma solução Office, a versão incorporada é registrada automaticamente. Se você publicou e instalou anteriormente a mesma [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] solução no seu computador de desenvolvimento, detecta que o caminho de instalação para a versão publicada e a versão construída são diferentes depois que a solução for construída, reconstruída ou publicada. A mensagem de erro diz que "a personalização não pode ser instalada porque outra versão está instalada no momento e não pode ser atualizada a partir deste local". As chaves de registro são atualizadas sempre que uma solução é reconstruída. Portanto, você deve desinstalar a versão anterior antes de publicar, depurar ou executar a nova versão.

 Para evitar que a mensagem apareça, crie outra conta de usuário em seu computador de desenvolvimento para testar sua implantação. Como alternativa, você pode desinstalar a versão da lista de programas instalados no computador antes de publicar, depurar ou reconstruir a solução.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Exceção não capturada ou erro de método não encontrado quando você instala uma solução
 Quando você instala as soluções do Office abrindo o manifesto de implantação (um arquivo *.vsto),* aplicativo do Office, documento ou pasta de trabalho, mensagens de erro para as seguintes condições podem aparecer:

- Método não encontrado.

- Missingmethodexception.

- Exceção não capturada.

  Para evitar essas mensagens de erro, instale a solução executando o programa Configuração.

  Quando você instala a solução sem executar o programa de configuração, o instalador não verifica ou instala pré-requisitos. O programa Configuração verifica a versão correta dos pré-requisitos e os instala conforme necessário.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Chaves de registro manifesto para alteração de add-ins depois que um projeto InstallShield Limited Edition é construído
 A chave de registro manifesto que faz parte de um programa de configuração adicional VSTO às vezes muda de *.vsto* para *.dll.manifest* quando você constrói um projeto InstallShield Limited Edition.

 Para contornar esse problema, crie o projeto InstallShield Limited Edition em uma solução diferente ou use O Nome da Empresa.AddinName como o valor da chave de registro que contém o nome do Add-in VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>O ClickOnce Installer para sua solução Office não instala os conjuntos de interop primários
 Quando você executa o programa de configuração que o ClickOnce cria para a solução office, o instalador dos PIAs (Office Primary Interop Assemblies, conjuntos de interops primários do Office) é executado somente se nenhum PIAs já estiver instalado.

 Se o programa de configuração não instalar os PIAs corretamente, instale-os manualmente executando o arquivo instalador chamado *o2007pia.msi* do diretório de instalação.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Reinstalar soluções do Office causa um argumento fora do intervalo de exceção
 Quando você reinstala uma <xref:System.ArgumentOutOfRangeException> solução office, uma exceção pode aparecer com a seguinte mensagem de erro: O argumento especificado estava fora do intervalo de valores válidos.

 Essa situação ocorre se o invólucro da URL para o local de instalação for diferente. Por exemplo, esse erro apareceria se `http://fabrikam.com/ExcelSolution.vsto` você instalasse `http://fabrikam.com/excelsolution.vsto` uma solução office da primeira vez e depois fosse usada na segunda vez.

 Para evitar que a mensagem apareça, use o mesmo invólucro ao instalar soluções do Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Não é possível instalar uma solução ClickOnce abrindo o manifesto de implantação da web
 Os usuários podem instalar soluções do Office abrindo o manifesto de implantação da web. No entanto, algumas instalações do Internet Information Services (IIS) bloqueiam a extensão do nome do arquivo *.vsto.* Você deve definir o tipo MIME no IIS antes de usá-lo para implantar uma solução office.

 Para obter informações sobre como definir o tipo MIME no IIS 7, consulte [Adicionar um tipo MIME (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Defina a extensão para **.vsto** e o tipo MIME como **aplicativo/x-ms-vsto**.

## <a name="see-also"></a>Confira também

- [Solucionar problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Implantar uma solução de Office](../vsto/deploying-an-office-solution.md)
