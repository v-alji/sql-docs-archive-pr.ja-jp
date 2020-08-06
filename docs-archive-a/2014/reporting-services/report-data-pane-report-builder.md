---
title: レポートデータペイン (レポートビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c87ee4411f5c1ec4c07e0fc9f0357f6fb33e3c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631601"
---
# <a name="report-data-pane-report-builder"></a>[レポート データ] ペイン (レポート ビルダー)
  **[レポート データ]** ペインを使用すると、レポート内で現在定義されているパラメーター、データ ソース、データセット、フィールド コレクション、および画像が表示されます。 [レポート データ] では、レポート内のデータを表すアイテムの階層ビューが表示されます。 最上位のノードは、組み込みフィールド、パラメーター、画像、およびデータ ソース参照を表します。 データ アイテムを表示するには、各ノードを展開します。 たとえば、データ ソース ノードを展開すると、そのデータ ソース用に定義されたデータセットが表示されます。 データセットを展開すると、そのフィールド コレクションが表示されます。 データをレポート ページ上の選択したレポート アイテムにリンクするには、アイテムをレポート デザイン画面または [グループ化] ペインにドラッグします。 詳細については、「[レポート デザイン ビュー &#40;レポート ビルダー&#41;](report-builder/report-design-view-report-builder.md)」を参照してください。

## <a name="options"></a>Options
 **組み込みフィールド**レポート名やページ番号など、レポートでよく使用されるフィールドを表します。 詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。

 **パラメーター**レポートパラメーターのコレクションを表します。各パラメーターには、単一値または複数値を指定できます。 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-design/report-parameters-report-builder-and-report-designer.md)にあります。

 **画像**レポートで使用されるイメージのセットを表します。 詳細については、「[画像 &#40;レポート ビルダーおよび SSRS& #41;](report-design/images-report-builder-and-ssrs.md)」を参照してください。

 **データソース**埋め込みデータソースまたは共有データソースへの参照を表します。 データ ソースは、レポートのデータのソースを表します。 データ ソースは、そのデータ ソースを使用するデータセットのコレクションの親ノードです。 詳細については、「[レポートにデータを追加する &#40;レポートビルダーと SSRS&#41;](report-data/report-datasets-ssrs.md) 」と「データ[接続、データソース、および接続レポートビルダー文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。

 **データセット**1つのコマンドを実行してデータソースから取得されるデータを表し [!INCLUDE[tsql](../includes/tsql-md.md)] ます。たとえば、データベースからデータを取得するクエリなど [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] です。 データセットは、クエリで指定されたフィールドのほか、計算フィールドも含むコレクションの親ノードです。 レポート ビルダーでは、クエリを指定できるようにクエリ デザイナーがサポートされています。 詳細については、「[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md)」を参照してください。

## <a name="see-also"></a>参照
 [データセットフィールドコレクション &#40;レポートビルダーおよび ssrs&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) [レポートビルダーダイアログボックス、ペイン、およびウィザードの](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)[グループ化ペイン &#40;](report-design/grouping-pane-report-builder.md)レポートビルダー&#41;&#40;[と SSRS のレポートの検索、表示、および管理](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)のヘルプレポートビルダー


