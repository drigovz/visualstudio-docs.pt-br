---
title: Publicar página, designer de projeto (desenvolvimento do Office)
description: Saiba como a página publicar do designer de projeto no Visual Studio é usada para configurar as propriedades de implantação.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc80a71516f1de8f2a6943d9df7b02341ea786aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971720"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Publicar página, designer de projeto (desenvolvimento do Office no Visual Studio)
  A página **publicar** do **Designer de projeto** é usada para configurar as propriedades de implantação.

 Para acessar essa página, selecione o projeto em **Gerenciador de soluções** e, no menu **projeto** , escolha **Propriedades** *ProjectName* . Se a página **publicar** não for exibida, escolha a guia **publicar** .

> [!NOTE]
> Você também pode definir o local de publicação no **Assistente** de publicação. Para obter mais informações, consulte [como publicar uma solução do Office usando o ClickOnce](/previous-versions/bb386095(v=vs.110)).

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Local da pasta de publicação (site, servidor FTP ou caminho do arquivo)** Necessário.

 O local da pasta de publicação é o diretório no qual o Visual Studio copia os arquivos da solução, como manifestos, assemblies e outros arquivos da compilação. Você deve ter acesso de gravação a esse diretório.

 As opções incluem o computador local, um compartilhamento de arquivos UNC ou um site da Web HTTP/HTTPS. O caminho pode ser local (*c:\foldername\publishfolder*), relativo (*publicação \\*) ou um local totalmente qualificado (*\\ \servername\foldername* ou http://<em>ServerName/nome_da_pasta</em>).

 Por padrão, o local de publicação é *http://localhost/projectname/* se você tiver o IIS instalado ou o diretório de *\\ publicação* se não tiver o IIS instalado.

 **URL da pasta de instalação** Adicional.

 A URL da pasta de instalação é o diretório do qual o usuário final irá instalar a personalização. Ele também é o caminho que será usado pela solução para verificar se há atualizações. O caminho pode ser o mesmo que o local da pasta de publicação, mas isso não é um requisito.

 As opções incluem o computador local, um compartilhamento de arquivos UNC ou um site da Web HTTP/HTTPS. O caminho pode ser local (*c:\foldername\publishfolder*), relativo (*publicação \\*) ou um local totalmente qualificado (*\\ \servername\foldername* ou http://<em>ServerName/nome_da_pasta</em>). Todos os locais HTTP/HTTPS devem ser criados com caracteres US-ASCII. Não há suporte para caracteres Unicode.

 Se o caminho de instalação for definido, os arquivos de personalização deverão estar nesse local para que os usuários instalem a personalização. O local deve ser definido somente se você souber o local de implantação final.

 Se os arquivos de instalação estiverem em um local relativo ao documento ou ao programa de instalação, como com a opção CD, deixe essa caixa em branco.

 Esse valor pode ser atribuído posteriormente por um administrador. Para obter mais informações, consulte [como alterar o caminho de instalação de uma solução do Office](/previous-versions/bb608626(v=vs.110)).

 **Pré-requisitos** Os pré-requisitos podem ser incluídos com o programa de instalação ou baixados sob demanda durante a instalação.

- **Baixar pré-requisitos do site do fornecedor do componente**: Use esta opção para baixar esses pré-requisitos da Microsoft.

- **Baixar pré-requisitos do mesmo local que o meu aplicativo**: Use esta opção para empacotar os pré-requisitos em seu instalador. A inclusão dos arquivos de pré-requisito com o programa de instalação aumenta o tamanho da solução.

- **Baixar pré-requisitos do seguinte local**: Use esta opção para disponibilizar os pré-requisitos para os usuários finais separadamente como outro programa de instalação em uma página da Web ou compartilhamento de rede.

  **Atualizações** do O intervalo de atualização determina a frequência com que a solução verifica se há atualizações. O padrão é verificar a cada sete dias.

  A verificação de atualizações sempre que uma personalização de nível de documento ou um suplemento do VSTO é carregado manteria a atualização, mas afetaria o desempenho da inicialização.

  Se você estiver implantando usando um CD ou uma unidade removível, defina isso para **nunca verificar se há atualizações**.

  **Opções (descrição)** As opções de publicação para as seguintes propriedades podem ser definidas:

- Idioma de publicação: a localidade da solução do Office.

- Nome do editor: o nome da empresa ou do desenvolvedor como ele aparece em **Adicionar/remover programas** ou **programas e recursos**.

- Nome do produto: o nome da solução do Office como ele aparece em **Adicionar/remover programas** ou **programas e recursos**.

- URL de suporte: o local para os usuários finais entrarem em contato com o suporte técnico para a solução do Office.

  **Opções (configurações do Office)** As opções de publicação para as seguintes propriedades podem ser definidas:

- Nome da solução: o nome da solução do Office como aparece no aplicativo do Office.

- Descrição: a descrição da solução do Office como ela aparece no aplicativo do Office.

- Comportamento de carregamento do suplemento do VSTO.

  - Carregar na inicialização: Especifica que o suplemento do VSTO é carregado quando o aplicativo do Office é iniciado.

  - Carregar sob demanda: Especifica que o suplemento do VSTO é carregado quando o aplicativo o exige, como quando um usuário clica em um elemento de interface do usuário que usa a funcionalidade no suplemento do VSTO.

  **Idioma da publicação** Essa opção define o idioma dos termos de licença para software Microsoft e inclui os pacotes de idiomas na lista de pré-requisitos. Ele não afeta o idioma da personalização. O idioma no programa de instalação é determinado pelos idiomas instalados do Visual Studio.

  Para obter mais informações sobre como alterar a **linguagem de publicação**, consulte [como alterar o idioma de publicação para um aplicativo ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Versão de publicação** Define o número de versão para a personalização. Quando o número de versão é alterado, o aplicativo é publicado como uma atualização. Uma nova pasta é criada para cada versão durante o processo de compilação para evitar a substituição da versão publicada anteriormente. Cada parte da versão de publicação (**principal**, **secundária**, **compilação** e **revisão**) pode conter até cinco dígitos.

  **Incrementar a revisão automaticamente com cada versão** Adicional. Quando selecionado (o padrão), a parte de **revisão** do número de versão é incrementada por um sempre que a personalização é publicada. Isso faz com que a personalização seja publicada como uma atualização.

  **Publicar agora** Publica o aplicativo usando as configurações atuais. Equivalente ao botão **concluir** no assistente de **publicação**.

## <a name="see-also"></a>Consulte também

- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
- [Implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Pré-requisitos da solução do Office para implantação](/previous-versions/bb608617(v=vs.110))