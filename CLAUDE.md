# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## リポジトリの構成

このディレクトリ (`claudework`) 自体は Git リポジトリではなく、独立した小規模アプリを集めた作業用ワークスペースです。各サブディレクトリが個別のプロジェクトであり、それぞれ別の GitHub リポジトリに対応します（対応していないものは新規作成が必要）。

- `quiz app/` — ドイツ語B1単語クイズアプリ（HTML/CSS/JS単一ファイル構成、フレームワークなし）。既存の Git リポジトリで、GitHub リモート `https://github.com/GebratenerReis/deutch_quizqpp.git` に接続済み。詳細は `quiz app/CLAUDE.md` を参照。
- `wearher/` — 東京の天気を表示する Node.js/Express アプリ。`server.js` が Express サーバーとして `/api/weather` エンドポイントを提供し、OpenWeatherMap API を呼び出す。APIキーは `.env` の `OPENWEATHERMAP_API_KEY` に設定（`.env.example` を参照）。まだ Git 管理されていない。
  - 起動: `cd wearher && npm install && npm start`（`http://localhost:3000` で起動）
- `index.html` — ルート直下の単純な挨拶ページ（単体で動作、ビルド不要）。
- `run-apps/` — 現状空のディレクトリ。

サブプロジェクトごとに技術スタックが異なるため、作業前に対象ディレクトリの構成・既存の `CLAUDE.md`（あれば）を確認すること。

## Git 運用ルール（最重要）

**コードを変更したら、その都度 GitHub にプッシュすること。** 変更を溜め込まず、意味のある単位（1機能・1修正ごと）でコミットし、都度リモートへ push する。

- 対象ディレクトリが Git 未初期化の場合は、変更前に `git init` とリモートリポジトリの設定要否をユーザーに確認する。
- コミット前に `git status` / `git diff` で差分を確認し、意図しないファイル（`.env` や `node_modules` など）が含まれていないことを確認する。
- push 前にリモート追跡ブランチの状態を確認し、force push など破壊的操作は行わない。
