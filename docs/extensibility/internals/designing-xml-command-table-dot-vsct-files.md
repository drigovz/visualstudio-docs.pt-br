---
title: Projetando tabela de comando XML (. Vsct) Arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708749"
---
# <a name="design-xml-command-table-vsct-files"></a>Design arquivos da tabela de comando XML (.vsct)
Um arquivo de tabela de comando XML *(.vsct)* descreve o layout e a aparência dos itens de comando para um VSPackage. Os itens de comando incluem botões, caixas de combinação, menus, barras de ferramentas e grupos de itens de comando. Este artigo descreve arquivos de tabela de comando XML, como eles afetam itens de comando e menus e como criá-los.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandos, menus, grupos e o arquivo .vsct
 Os arquivos *.vsct* são organizados em torno de comandos, menus e grupos de comando. As tags XML no arquivo *.vsct* representam cada um desses itens, juntamente com outros itens associados, como botões de comando, posicionamento de comando e bitmaps.

 Quando você cria um novo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage executando o modelo do pacote, o modelo gera um arquivo *.vsct* com os elementos necessários para um comando de menu, janela de ferramenta ou editor personalizado, dependendo de suas seleções. Este arquivo *.vsct* pode então ser modificado para atender aos requisitos de um VSPackage específico. Para exemplos de como modificar um arquivo *.vsct,* consulte [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

 Para criar um novo arquivo *.vsct* em branco, consulte [Como: Criar um arquivo *.vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Uma vez criado, você adiciona elementos, atributos e valores XML ao arquivo para descrever o layout do item de comando. Para obter um esquema XML detalhado, consulte a referência do [esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Diferenças entre arquivos .ctc e .vsct
 Embora o significado por trás das tags XML em um arquivo *.vsct* seja o mesmo que as tags no formato de arquivo *.ctc* agora depreciado, sua implementação é um pouco diferente:

- A nova [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ** \<tag extern>** é onde você faz referência a outros arquivos *.h* a serem compilados, como aqueles arquivos para a barra de ferramentas.

- Embora os arquivos *.vsct* suportem a declaração **/incluir,** como os arquivos *.ctc* fazem, ele também apresenta um novo ** \<** elemento de importação>. A diferença é que **/incluir** traz *todas as* informações, enquanto ** \<a importação>** traz apenas os nomes.

- Embora os arquivos *.ctc* exijam um arquivo de cabeçalho no qual você define suas diretivas de pré-processador, um não é necessário para arquivos *.vsct.* Em vez disso, coloque suas diretivas na ** \<** tabela de símbolos, localizada no símbolo>elementos, localizado na parte inferior do arquivo *.vsct.*

- Os arquivos *.vsct* apresentam uma ** \<tag>Anotação,** que permite incorporar qualquer informação que você goste, como notas ou até mesmo imagens.

- Os valores são armazenados como atributos no item.

- Os sinalizadores de comando podem ser armazenados individualmente ou empilhados.  O IntelliSense, no entanto, não funciona em bandeiras de comando empilhadas. Para obter mais informações sobre bandeiras de comando, consulte o [elemento CommandFlag](../../extensibility/command-flag-element.md).

- Você pode especificar vários tipos, como dropdowns divididos, combos, etc.

- GuiDs não validam.

- Cada elemento de UI tem uma string que representa o texto que é exibido com ele.

- O pai é opcional. Se omitido, o valor *Grupo Desconhecido* é usado.

- O *argumento Ícone* é opcional.

- Seção Bitmap: Esta seção é a mesma de um arquivo *.ctc,* exceto que agora você pode especificar um nome de arquivo via Href que será puxado pelo compilador *vsct.exe* na hora da compilação.

- ResID: O iD de recurso do bitmap antigo pode ser usado e ainda funciona o mesmo que em arquivos *.ctc.*

- HRef: Um novo método que permite especificar um nome de arquivo para o recurso bitmap. Ele assume que todos são usados, para que você possa omiti-lo a seção Usado. O compilador primeiro procurará recursos locais para o arquivo, depois em quaisquer ações líquidas e quaisquer recursos definidos pelo **switch /I.**

- Encadernação de tecla: Você não precisa mais especificar um emulador. Se você especificar um, o compilador assumirá que o editor e o emulador são os mesmos.

- Keychord: Keychord foi derrubado. O novo formato é *Key1,Mod1,Key2,Mod2*.  Você pode especificar um caractere, hexadecimal ou uma constante de VK.

O novo compilador, *vsct.exe,* compila arquivos *.ctc* e *.vsct.* O antigo compilador *ctc.exe,* no entanto, não reconhecerá ou compilará arquivos *.vsct.*

Você pode usar o compilador *vsct.exe* para converter um arquivo *.cto* existente em um arquivo *.vsct.* Para obter mais informações, consulte [Como: Criar um arquivo .vsct a partir de um arquivo .cto existente](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Os elementos do arquivo .vsct
 A tabela de comando tem a seguinte hierarquia e elementos:

- [Elemento Tabela de comando :](../../extensibility/commandtable-element.md)Representa todos os comandos, grupos de menus e menus associados ao VSPackage.

- [Elemento extern :](../../extensibility/extern-element.md)Faz referência a quaisquer arquivos externos .h que você deseja mesclar com o arquivo *.vsct.*

- [Inclua elemento](../../extensibility/include-element.md): Referencia todos os arquivos adicionais de cabeçalho (.h) que você deseja compilar juntamente com o seu arquivo *.vsct.* Um arquivo *.vsct* pode incluir arquivos *.h* contendo constantes que definem comandos, grupos de menus e menus que o IDE ou outro VSPackage fornece.

- [Elemento comandos](../../extensibility/commands-element.md): Representa todos os comandos individuais que podem ser executados. Cada comando tem os seguintes quatro elementos infantis:

- [Elemento menus](../../extensibility/menus-element.md): Representa todos os menus e barras de ferramentas no VSPackage. Os menus são recipientes para grupos de comandos.

- [Elemento grupos](../../extensibility/groups-element.md): Representa todos os grupos no VSPackage. Grupos são coleções de comandos individuais.

- [Elemento botões](../../extensibility/buttons-element.md): Representa todos os botões de comando e itens de menu no VSPackage. Botões são controles visuais que podem ser associados a comandos.

- [Elemento Bitmaps](../../extensibility/bitmaps-element.md): Representa todos os bitmaps para todos os botões no VSPackage. Bitmaps são imagens exibidas ao lado ou nos botões de comando, dependendo do contexto.

- [Elemento Comandos :](../../extensibility/commandplacements-element.md)Indica locais adicionais onde os comandos individuais devem estar localizados nos menus do seu VSPackage.

- [Elemento De visibilidadeRestrições](../../extensibility/visibilityconstraints-element.md): Especifica se um comando é exibido em todos os momentos ou apenas em determinados contextos, como quando uma caixa de diálogo ou janela específica é exibida. Menus e comandos que tenham um valor para este elemento serão exibidos somente quando o contexto especificado estiver ativo. O comportamento padrão é exibir o comando o tempo todo.

- [Elemento Tecelandernações](../../extensibility/keybindings-element.md): Especifica quaisquer vinculações de tecla para os comandos. Ou seja, uma ou mais combinações de chaves que devem ser pressionadas para executar o comando, como **Ctrl**+**S**.

- [Elemento UsedCommands](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Informa ao ambiente que, embora o comando especificado seja implementado por outro código, quando o VSPackage atual estiver ativo, ele fornece a implementação do comando.

- [Elemento símbolos](../../extensibility/symbols-element.md): Contém os nomes dos símbolos e os IDs GUID para todos os seus comandos no pacote.

## <a name="vsct-file-design-guidelines"></a>.vsct diretrizes de design de arquivos
 Para projetar com sucesso um *arquivo .vsct,* siga essas diretrizes.

- Os comandos podem ser colocados apenas em grupos, grupos podem ser colocados apenas em menus e menus podem ser colocados apenas em grupos. Apenas menus são exibidos no IDE, grupos e comandos não são.

- Os submenus não podem ser atribuídos diretamente a um menu, mas devem ser atribuídos a um grupo, que por sua vez é atribuído a um menu.

- Comandos, submenus e grupos podem ser atribuídos a um grupo ou menu de pais usando o campo pai de sua diretiva definitiva.

- Organizar uma tabela de comando somente através dos campos-mãe nas diretivas tem uma limitação significativa. As diretivas que definem objetos podem ter apenas um argumento pai.

- Reutilizar comandos, grupos ou submenus requer o uso de uma nova diretiva `GUID:ID` para criar uma nova instância do objeto com seu próprio par.

- Cada `GUID:ID` par deve ser único. Reutilizar um comando que tenha sido colocado em um menu, uma barra de ferramentas ou <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> em um menu de contexto, é manuseado pela interface.

- Comandos e submenus também podem ser atribuídos a vários grupos, e grupos podem ser atribuídos a vários menus usando o [elemento Comandos](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Notas de arquivo .vsct
 Se você fizer qualquer alteração em um arquivo *.vsct* depois de compilá-lo e colocá-lo em um DLL de satélite nativo, você **devenv.exe /setup /nosetupvstemplates**. Isso força os recursos do VSPackage especificados no registro experimental a serem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] releituras e o banco de dados interno que descreve a ser reconstruído.

 Durante o desenvolvimento, é possível que vários projetos VSPackage sejam criados e registrados na colmeia de registro experimental que pode levar a uma confusão confusa no IDE. Para corrigir isso, você pode redefinir a colmeia experimental para as configurações padrão para remover todos os VSPackages registrados e quaisquer alterações que eles possam ter feito para o IDE. Para redefinir a colmeia experimental, use a ferramenta CreateExpInstance.exe que vem com o Visual Studio SDK. Você pode encontrá-lo em:

 *%PROGRAMFILES(x86)%\Versão\\\<do Estúdio Visual> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Execute a ferramenta usando o comando **CreateExpInstance /Reset**. Lembre-se que esta ferramenta remove da colmeia experimental todos os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackages registrados normalmente não instalados com .

## <a name="see-also"></a>Confira também
- [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md)
