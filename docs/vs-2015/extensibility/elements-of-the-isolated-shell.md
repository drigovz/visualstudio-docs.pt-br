---
title: Elementos do Shell isolado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204608"
---
# <a name="elements-of-the-isolated-shell"></a>Elementos do Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode modificar as configurações do registro, as configurações de tempo de execução e o ponto de entrada do aplicativo de seu aplicativo de shell isolado e seus arquivos. vsct,. pkgdef e. pkgundef.  
  
## <a name="registry-settings"></a>Configurações do Registro  
 Os arquivos. pkgdef e. pkgundef modificam as configurações do registro para o aplicativo de shell isolado. Quando o aplicativo é executado, as configurações do registro são definidas na seguinte sequência:  
  
 Quando o aplicativo é executado, as configurações do registro são definidas na seguinte sequência:  
  
1. A chave do registro para o aplicativo é criada.  
  
2. O registro é atualizado do arquivo. pkgdef do aplicativo definindo chaves e entradas especificadas.  
  
3. Para cada pacote que faz parte do seu aplicativo, o registro é atualizado do arquivo. pkgdef do pacote. Cada pacote é definido no arquivo. pkgdef do aplicativo pela chave $RootKey $ \Packages \\ {*vsPackageGuid*} para o pacote.  
  
4. O registro é atualizado a partir de AppEnvConfig. pkgdef e BaseConfig. pkgdef no diretório \Common7\IDE\ShellExtensions\Platform do *caminho de instalação do SDK do Visual Studio*. Esses arquivos fazem parte do Visual Studio e também fazem parte do pacote redistribuível do shell do Visual Studio (modo isolado).  
  
5. O registro é atualizado do arquivo. pkgundef do aplicativo removendo as chaves e entradas especificadas.  
  
## <a name="run-time-settings"></a>Configurações de tempo de execução  
 Quando um usuário inicia o aplicativo de shell isolado, ele chama o ponto de entrada inicial do shell do Visual Studio. As configurações do aplicativo são definidas quando o aplicativo é iniciado, da seguinte maneira:  
  
1. O Shell do Visual Studio verifica o registro do aplicativo em busca de chaves específicas. Se a configuração de uma chave for especificada na chamada para o ponto de entrada inicial, esse valor substituirá o valor no registro.  
  
2. Se nem o registro nem o parâmetro de ponto de entrada especificar o valor de uma configuração, o valor padrão para a configuração será usado.  
  
   Quando um usuário inicia seu aplicativo na linha de comando, todas as opções de linha de comando são passadas para o Shell do Visual Studio, que os trata da mesma maneira que o devenv. Para obter mais informações sobre os comutadores do devenv, consulte [Opções de linha de comando](../ide/reference/devenv-command-line-switches.md) do devenv e [Opções de linha de comando do devenv para o desenvolvimento de VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Para obter mais informações sobre como um pacote se registra para opções de linha de comando, consulte [adicionando opções de linha de comando](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>O ponto de entrada inicial  
 O arquivo de Appenvstub.dll contém pontos de entrada para acessar o Shell isolado. Quando o aplicativo é iniciado, ele chama o ponto de entrada inicial de Appenvstub.dll.  
  
 Você pode alterar o comportamento do aplicativo alterando o valor do último parâmetro que é passado para o ponto de entrada inicial. Para obter mais informações, consulte [parâmetros do ponto de entrada do Shell isolado (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Dos. Arquivo vsct  
 O arquivo. vsct permite especificar quais elementos padrão da interface do usuário do Visual Studio estão disponíveis no aplicativo. Para obter mais informações, consulte [. Arquivos vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Dos. Arquivo Pkgundef  
 Quando o aplicativo é instalado em um computador no qual o Visual Studio já está instalado, uma cópia das entradas de registro do Visual Studio é feita para o aplicativo. Por padrão, o aplicativo usa VSPackages que já estão instalados no computador. O arquivo. pkgundef permite que você exclua entradas de registro para remover elementos específicos do Shell ou das extensões do Visual Studio do aplicativo. Para obter mais informações, consulte [. Arquivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 O arquivo. pkgundef permite que você exclua entradas de registro para remover elementos específicos do Shell ou das extensões do Visual Studio do aplicativo. Para obter mais informações, consulte [. Arquivos Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 O conjunto de GUIDs de pacote que você pode excluir está listado em [GUIDs de pacote de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Dos. Arquivo pkgdef  
 O arquivo. pkgdef permite definir entradas de registro para o aplicativo que são definidos quando o aplicativo é instalado. Para obter uma descrição do arquivo. pkgdef e uma lista de entradas do registro que o Shell do Visual Studio usa, consulte [. Arquivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Cadeias de caracteres de substituição  
 As cadeias de caracteres de substituição usadas nos arquivos. pkgdef e. pkgundef são listadas em [cadeias de substituição usadas no. Pkgdef e. Arquivos Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Outras configurações  
 Se o aplicativo de shell isolado depender de Microsoft.VisualStudio.GraphModel.dll, você precisará adicionar o redirecionamento de associação a seguir ao arquivo. config do aplicativo de shell isolado:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
