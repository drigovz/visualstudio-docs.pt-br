---
title: Implantando páginas iniciais personalizadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712234"
---
# <a name="deploy-custom-start-pages"></a>Implantar páginas iniciais personalizadas

Você pode implantar páginas iniciais personalizadas usando a implantação do VSIX ou copiando os arquivos para os locais corretos no computador de destino.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implantação do VSIX usando o modelo de projeto Iniciar página

Quando você cria uma página inicial usando o modelo de projeto Iniciar página e, em seguida, constrói o projeto, o Visual Studio cria um arquivo *.vsix* que você pode distribuir. A embalagem de uma página inicial em um arquivo *.vsix* oferece as seguintes opções de implantação, dependendo do seu público-alvo:

- Você pode colocar o arquivo *.vsix* em um compartilhamento de rede ou em um site público. Quando alguém abre o arquivo, a Página inicial é instalada automaticamente.

- Você pode carregar o arquivo *.vsix* para o site [do Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que os usuários possam instalá-lo usando o Extension **Manager**.

O modelo de projeto Página Inicial cria uma cópia da página inicial padrão do Visual Studio para que você possa modificar a cópia e preservar a original.

Você pode obter o modelo de projeto Iniciar página usando **o Extension Manager** ou baixando-o no site da Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implantação do VSIX sem usar o modelo de projeto Iniciar página
 Uma implantação VSIX bem-sucedida requer que uma extensão seja instalada em pastas que são reconhecidas pelo processo de registro VSIX e pelo **Extension Manager**. Como o modelo de projeto Página Inicial já especifica as pastas corretas, recomendamos que você a use sempre que quiser empacotar uma extensão para implantação do VSIX. No entanto, se você tiver um caso em que você não pode usar o modelo, você pode criar uma implantação VSIX sem usá-lo.

 Para criar uma implantação VSIX sem usar o modelo de projeto Iniciar página, primeiro crie um arquivo *.vsix* para a Página Inicial em qualquer uma dessas duas maneiras:

- Adicionando seus arquivos personalizados de Página Inicial a um Projeto VSIX vazio. Para obter mais informações, consulte [o modelo do projeto VSIX](../extensibility/vsix-project-template.md).

- Criando manualmente um arquivo *.vsix.* Para criar um arquivo *.vsix* manualmente:

   1. Crie o arquivo *extension.vsixmanifest* e o arquivo *[Content_Types].xml* em uma nova pasta. Para obter mais informações, consulte [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. No Windows Explorer, clique com o botão direito do mouse na pasta que contém os dois arquivos XML, clique **em Enviar para**e, em seguida, clique em Compactado (zíper). Renomeie o arquivo *.zip* resultante para *Filename.vsix*, onde Filename é o nome do arquivo redisível que instala seu pacote.

Para que o Visual Studio `Content Element` reconheça uma página inicial, `CustomExtension Element` o `Type` manifesto VSIX deve conter um que tenha o atributo definido como `"StartPage"`. Uma extensão de página inicial que foi instalada usando a implantação vSIX aparece na lista **Personalizar página inicial** na página de opções de **inicialização** como Nome de *extensão* **[Extensão instalada]** .

Se o pacote Iniciar página incluir conjuntos, você deve adicionar o registro do caminho de vinculação para que eles estejam disponíveis quando o Visual Studio for iniciado. Para fazer isso, certifique-se de que seu pacote inclua um arquivo *.pkgdef* que tenha as seguintes informações.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Implantação vsix para todos os usuários
 Por padrão, as extensões implantadas nos pacotes VSIX são instaladas apenas para o usuário atual. Você pode fazer uma instalação de Página Inicial para todos os usuários da máquina de destino criando uma implantação All-Users.

### <a name="to-create-an-all-users-deployment"></a>Para criar uma implantação de todos os usuários

1. Abra o arquivo *extension.vsixmanifest* na exibição de código.

2. No `Identifier` elemento do manifesto vsix, `AllUsers` adicione um elemento `true`que tenha um valor de .

    ```
    <AllUsers>true</AllUsers>
    ```

     Isso faz com que o instalador vsix solicitar ás permissões de administrador e, em seguida, instale os arquivos em *\Common7\IDE\Extensões*.

3. Abra o arquivo *.pkgdef.*

4. Modifique o *.pkgdef* para definir a página inicial padrão em HKLM adicionando o seguinte, onde *MyStartPage.xaml* é o nome do arquivo *.xaml* que contém sua Página Inicial.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Isso diz ao Visual Studio para olhar na nova localização da Página inicial.

## <a name="file-copy-deployment"></a>Implantação de cópia de arquivo
 Você não precisa criar um arquivo *.vsix* para implantar uma página inicial personalizada. Em vez disso, você pode copiar a marcação e o suporte de arquivos diretamente na <em>pasta \StartPages\* do usuário. A * Personalizar a lista*de páginas iniciais</em> * na página de opções **de inicialização** lista todos os arquivos *.xaml* nessa pasta, juntamente com o caminho — por exemplo, *%USERPROFILE%\Meus documentos\Visual Studio {version}\StartPages\\{File Name}.xaml*. Se sua página inicial incluir referências a assembléias privadas, você deve copiá-las e colá-las na pasta *\PrivateAssemblies.\*

 Para distribuir uma Página inicial que você criou sem empacotá-la em um arquivo *.vsix,* recomendamos que você use uma estratégia básica de cópia de arquivo, por exemplo, um script em lote ou qualquer outra tecnologia de implantação que permite colocar os arquivos nos diretórios necessários.

### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente uma página inicial personalizada

1. Copie o arquivo *.xaml* que contém a marcação Iniciar página, juntamente com quaisquer arquivos de suporte\* que não sejam conjuntos e cole-os na pasta *\StartPages do usuário.

2. Se a página inicial exigir montagens, copie-as e cole-as em *.. {Pasta de instalação do Visual Studio}\Common7\IDE\PrivateAssemblies\\. \\*

3. Na **lista Personalizar a página inicial** na página de opções de **inicialização,** selecione a nova Página inicial. Para obter mais informações, consulte [Personalizar a página inicial](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Confira também

- [Personalize a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)
- [Adicione o controle do usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)
