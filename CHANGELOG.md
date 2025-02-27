# Changelog

## [1.0.3](https://github.com/woodpecker-ci/woodpecker/releases/tag/v1.0.3) - 2023-10-14

* SECURITY
  * Update dependencies (#2587)
  * Frontend: bump postcss to 8.4.31 (#2541)
  * Check permissions on repo lookup (#2358)
  * Change token logging to trace level (#2247) (#2248)
* BUGFIXES
  * Fix gitlab hooks (#2537) (#2542)
  * Trim last "/" from WOODPECKER_HOST config (#2538) (#2540)
  * Fix(server/api/repo): Fix repair webhook host (#2372) (#2452)
  * Show correct event in pipeline step list (#2448)
  * Make WOODPECKER_MIGRATIONS_ALLOW_LONG have an actuall effect (#2251) (#2309)
  * Docker build dont ignore ci env vars (#2238) (#2246)
  * Handle parsed hooks that should be ignored (#2243) (#2244)
  * Return 204 not 500 on filtered pipeline (#2230)
  * Set correct version for release branch releases (#2227) (#2229)
* MISC
  * Rebuild swagger with latest version (#2455)

## [1.0.2](https://github.com/woodpecker-ci/woodpecker/releases/tag/v1.0.2) - 2023-08-16

* SECURITY
  * Validate webhook before change any data (#2221) (#2222)
* BUGFIXES
  * Bump default git clone plugin (#2215) (#2220)
  * Show all steps (#2190) (#2191)

## [1.0.1](https://github.com/woodpecker-ci/woodpecker/releases/tag/v1.0.1) - 2023-08-08

* SECURITY
  * Fix WOODPECKER_GRPC_VERIFY being ignored (#2077) (#2082)
* BUGFIXES
  * Fix 'add-orgs' migration (#2117) (#2145)
  * Fix UI and backend paths with subpath (#1799) (#2133)
  * Fix swagger response code (#2119) (#2121)
  * Forge Github Org: Use `login` instead of `name` (#2104) (#2106)
  * Client.go: Backport fix RepoPost path (#2100)
  * Fix translation key (#2098)

## [1.0.0](https://github.com/woodpecker-ci/woodpecker/releases/tag/v1.0.0) - 2023-07-29

* BREAKING
  * Use IDs to access organizations (#1873)
  * Drop support for Bitbucket Server (#1994)
  * Rename yaml `pipeline` to `steps` (#1833)
  * Drop ".drone.yml" as default pipeline config (#1795)
  * Build-in Env Vars, use _URL for all links/URLs (#1794)
  * Resolve built-in variables for global when filtered too (#1790)
  * Drop "Gogs" support (#1752)
  * Access repos by their IDs (#1691)
  * Drop "coding" support (#1644)
  * Add queue details UI for admins (#1632)
  * Remove `command:` from steps (#1032)
  * Remove old `build` API routes (#1283)
  * Let single line command be a single command (#1009)
  * Drop deprecated environment vars (#920)
  * Drop Var-Args in steps in favor of settings (#919)
  * Fix branch condition on tags (#917)
  * Use asymmetric key to sign webhooks (#916)
  * Add agent tagging / filtering for pipelines (#902)
  * Delete old fallback for "drone.sqlite" (#791)
  * Migrate to certmagic (#360)
* FEATURES
  * Implement YAML Map Merge, Overrides, and Sequence Merge Support (#1720)
  * Add users UI for admins (#1634)
  * Add agent no-schedule flag (#1567)
  * Change locale in user settings (#1305)
  * Add when evaluate filter (#1213)
  * Store an agents list and add agent heartbeats (#1189)
  * Add ability to trigger manual builds (#1156)
  * Add default event filter (#1140)
  * Add CLI support for global and organization secrets (#1113)
  * Allow multiple when conditions (#1087)
  * Add syntax highlighting for pipeline config (#1082)
  * Add `logs` command to CLI & update forges features docs (#1064)
  * Add method to check organization membership (#1037)
  * Global and organization secrets (#1027)
  * Add pipeline log output download (#1023)
  * Provide global environment variables for pipeline substitution (#968)
  * Add cron jobs (#934)
  * Support localized web UI (#912)
  * Add support to define a custom docker network and enable docker ipv6 (#893)
  * Add SSH backend (#861)
  * Add support for superseding runs (#831)
  * Add support for steps to be a list (instead of dict) (#826)
  * Add editing of secrets and registries (#823)
  * Allow loading sensitive flags from files (#815)
  * Add support for pipeline configuration service (#804)
  * Support all backends for CLI exec (#801)
  * Add support for pipeline root.when conditions (#770)
  * Add support to run pipelines using a local backend (#709)
  * Add initial version of Kubernetes backend (#552)
* SECURITY
  * Fix ignoring server set pipeline max-timeout (#1875)
  * Only grant privileged to plugins (#1646)
  * Only inject netrc to trusted clone plugins (#1352)
  * Support plugin-only secrets (#1344)
  * Fix insecure /tmp usage in local backend (#872)
* BUGFIXES
  * Handle case where there is no latest pipeline for GetBadge (#2042) (#2050)
  * Fix repo gate protection (#1969)
  * Make secrets with "/" in name editable / deletable (#1938)
  * Fix Bitbucket implement missing features (#1887) (#1889)
  * Fix nil pointer in repo repair (#1804)
  * Do not use OAuth client without token (#1803)
  * Correct label argument parsing in agent code (#1717)
  * Fully support `.yaml` (#1713)
  * Consistent status on delete (#1703)
  * Fix Bitbucket Server branches (#1698)
  * Set 'HOME' during local pipeline step (#1686)
  * Pipeline compiler: handle nil entrys in settings list (#1626)
  * Fix: backend auto-detection should be consistent (#1618)
  * Return 404 on badge endpoint for inactive repos (#1600)
  * Ensure the SharedInformerFactory closes eventually (#1585)
  * Deduplicate step docker container volumes (#1571)
  * Don't require secret value on secret edit (#1552) (#1553)
  * Rework status constraint logic for successes (#1515)
  * Don't panic on hook parsing (#1501)
  * Hide not owned repos from sidebar and repo list (#1453)
  * Fix cut of woodpecker animation (#1402)
  * Fix approval on mobile (#1320)
  * Unify buttons, links and improve focus styles (#1317)
  * Fix pipeline manual trigger on web (#1307)
  * Fix SCM visibility if user visibility is private (#1217)
  * Hide log output container if step does not have logs (#1086)
  * Fix to show build pipeline parse error (#1066)
  * Pipeline compiler should not alter specified image (#1005)
  * Gracefully handle non-zero exit code in local backend (#1002)
  * Replace run_on references with runs_on (#965)
  * Set default logging value of CLI to info (#871)
  * Support conditional branch as an array to align with documentation (#836)
  * Fix redirect after login (#824)
* ENHANCEMENTS
  * Add BranchHead implementation for bitbucket forge (#2011)
  * Use global logger for xorm logs and add options (#1997)
  * Let HookParse func explicit ignore events (#1942)
  * Link swagger in navbar (#1984)
  * Add option to read grpc-secret from file (#1972)
  * Let pipeline-compiler export step types (#1958)
  * docker backend use uuid instead of name as identifier (#1967)
  * Kubernetes do not set Pod's Image pull policy if not explicitly set (#1914)
  * Fixed when:evaluate on non-standard (non-CI*) env vars (#1907)
  * Add pull-request implementation for bitbucket forge (#1889)
  * Store agent ID in config file (#1888)
  * Fix bitbucket forge add repo (#1887)
  * Added Woodpecker Host Config used for Webhooks (#1869)
  * Drop old columns (#1838)
  * Remove MSSQL specific code and cleanups (#1796)
  * Remove unused file system API (#1791)
  * Add Forge Metadata to built-in environment variables (#1789)
  * Redirect to new pipeline (#1761)
  * Add reset token button (#1755)
  * Add agent functions to go-sdk (#1754)
  * Always send a status back to forge (#1751)
  * Allow to configure listener port for SSL (#1735)
  * Identify users using their remote ID (#1732)
  * Let agent retry to connecting to server (#1728)
  * Stable sort order for DB lists (#1702)
  * Add backend label to agents (#1692)
  * Web: use i18n-t to avoid v-html directive (#1676)
  * Various UI improvements (#1663)
  * Do not store inactive repos without any resources (#1658)
  * Implement visual display of queue statistics (#1657)
  * Agent check gRPC version against server (#1653)
  * Initiate Pagination Implementation for API and Infinite Scroll in UI (#1651)
  * Add PR pipeline list (#1641)
  * Save agent-id for tasks and add endpoint to get agent tasks (#1631)
  * Return 404 if pipeline not exist and handle 404 errors in WebUI (#1627)
  * UI should confirm secret deletion (#1604)
  * Add collapsable support to panel elements (#1601)
  * Add cancel button on secrets tab (#1599)
  * Allow custom dnsConfig in agent deployment (#1569)
  * Show platform, backend and capacity as badges in agent list (#1568)
  * Define WOODPECKER_FORGE_TIMEOUT server config (#1558)
  * Sort repos by org/name (#1548)
  * Improve button and input contrast in dark mode (#1456)
  * Consistent and more descriptive naming of parameters in index.ts (#1455)
  * Add button in UI to trigger the deployment event (#1415)
  * Use icons for step and workflow states (#1409)
  * Match notification font size to rest of the UI (#1399)
  * Support .yaml as file-ending for workflow config too (#1388)
  * Show workflow state in UI and collapse completed workflows (#1383)
  * Use pipeline wrapper and improve scaffold UI (#1368)
  * Lazy load locales (#1362)
  * Always use rounded quadrat user avatars (#1350)
  * Fix display of long pipeline and job names (#1346)
  * Support changed files for Gitea PRs (#1342)
  * Allow to change directory for steps (#1329)
  * UI use system font stack (#1326)
  * Add pull request labels as environment variable (#1321)
  * Make pipeline workflows collapsable (#1304)
  * Make submit buttons green and add forms (#1302)
  * Add pipeline build number into Pipeline list (#1301)
  * Add title to docs links (#1298)
  * Check if repo exists before creating pipeline (#1297)
  * Use HTML buttons to allow keyboard navigation (#1242)
  * Introduce and use Pagination helper func (#1236)
  * Sort secret lists and events (#1223)
  * Add support sub-settings and secrets in sub-settings (#1221)
  * Add option to ignore failures on steps (#1219)
  * Set a default value for `pipeline-event` flag of `cli exec` command (#1212)
  * Add option for docker runtime to provide default volumes (#1203)
  * Make healthcheck port configurable (#1197)
  * Don't show "changed files" if event can't have them (#1191)
  * Add dedicated DroneCI env compatibility layer (#1185)
  * Only enable debug endpoints if log level is debug or below (#1160)
  * Sort pipelines based on creation date (#1159)
  * Add option to turn on and off log automatic scrolling (#1149)
  * Checkout tags on tag pipeline (#1110)
  * Use fixed version of git clone plugin (#1108)
  * Fetch repositories with remote ID if possible (#1078)
  * Support Docker credential helpers (#1075)
  * Do not show pipeline name if it's a single file (#1069)
  * Remove xterm and use ansi converter for logs (#1067)
  * Update jsonschema and define "services" (#1036)
  * Show forge icons in UI (#987)
  * Make pipeline runtime log with description (#970)
  * Improve UI colors to have more contrast (#943)
  * Add branches support for BitBucket (#907)
  * Auto cancel blocked pipelines (#905)
  * Allow to change forge status messages (#900)
  * Added support for step errors when executing backend (#817)
  * Do not filter on linux/amd64 per default (#805)
* DOCUMENTATION
  * Remove never implemented "tag"-filter and document "ref"-filter to do the same (#1820)
  * Define Glossary (#1800)
  * Add more documentation about branch matching (#1186)
  * Use versioned docs (#1145)
  * Add gitpod setup (#1020)
* MISC
  * Drop tarball release (#1819)
  * Move helm charts to own repo "helm" (#1589)
  * Replace yarn with pnpm (#1240)
  * Publish preview docker images of pulls (#1072)

## [0.15.11](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.11) - 2023-07-12

* SECURITY
  * Update github.com/gin-gonic/gin to 1.9.1 (#1989)
* ENHANCEMENTS
  * Allow gitea dev version (#914) (#1988)

## [0.15.10](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.10) - 2023-07-09

* SECURITY
  * Fix agent auth (#1952) (#1953)
  * Return after error (#1875) (#1876)
  * Update github.com/docker/distribution (#1750)

## [0.15.9](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.9) - 2023-05-11

* SECURITY
  * Backport securitycheck and bump deps where needed (#1745)

## [0.15.8](https://github.com/woodpecker-ci/woodpecker/releases/tag/0.15.8) - 2023-04-29

* BUGFIXES
  * Use codeberg.org/6543/go-yaml2json (#1719)
  * Fix faulty hardlink in release tarball (#1669) (#1671)
  * Persist `DepStatus` of tasks (#1610) (#1625)

## [0.15.7](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.7) - 2023-03-14

* SECURITY
  * Update dependencies golang/x libs (#1612) (#1621)
* BUGFIXES
  * Docker backend should not close 'engine.Tail' result (#1616) (#1620)
  * Force pure Go resolver onto server (#1502) (#1503)
* ENHANCEMENTS
  * SanitizeParamKey "-" to "_" for plugin settings (#1511)
* MISC
  * Bump xgo and go to v1.19.5 (#1538) (#1547)
  * Pin official default clone image (#1526) (#1534)

## [0.15.6](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.6) - 2022-12-23

* SECURITY
  * Update golang.org/x/net (#1494)
  * [**BREAKING**] Disable metrics access if no token is set (#1469) (#1470)
  * Update dep moby (#1263) (#1264)
* BUGFIXES
  * Update json schema for cli lint to cover valid cases (#1384)
  * Add pipeline.step.when.branch string-array type to schema.json (#1380)
  * Display system CA error only if there is an error (#870) (#1286)
* ENHANCEMENTS
  * Bump Frontend Deps and remove unused (#1404)

## [0.15.5](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.5) - 2022-10-13

* BUGFIXES
  * Change build message column type to text (#1252) (#1253)
* ENHANCEMENTS
  * Bump DefaultCloneImage version to v1.6.0 (#1254)
  * On Repo update, keep old "Clone" if update would empty it (#1170) (#1195)

## [0.15.4](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.4) - 2022-09-06

* BUGFIXES
  * Extract commit message from branch creation (#1150) (#1153)
  * Respect WOODPECKER_GITEA_SKIP_VERIFY (#1152) (#1151)
  * update golang.org/x/crypto (#1124)
  * Implement Refresher for GitLab (#1031) (#1120)
  * Make returned proc list to be returned always in correct order (#1060) (#1065)
  * Update type of 'log_data' from blob to longblob (#1050) (#1052)
  * Make ListItem component more accessible by using a button tag when clickable (#1044) (#1046)
* MISC
  * Update base images (#1024) (#1025)

## [0.15.3](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.3) - 2022-06-16

* SECURITY
  * Update github.com/containerd/containerd (#978) (#980)
* BUGFIXES
  * Return to page after clicking login at navbar (#975) (#976)

## [0.15.2](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.2) - 2022-06-14

* BUGFIXES
  * Fix uppercase from_secrets (#842) (#925)
  * Fix key/val format for dind env vars (#889) (#890)
  * Update helm chart releasing (#882) (#888)
* DOCUMENTATION
  * Fix run_on references with runs_on in docs (#965)

## [0.15.1](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.1) - 2022-04-13

* SECURITY
  * Escape html / xml in log view (#879) (#880)
* FEATURES
  * Build multiarch images for server (#821) (#822)
* BUGFIXES
  * Branch list enhancements (#808) (#809)
  * Get Netrc machine from clone url (#800) (#803)

## [v0.15.0](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.15.0) - 2022-02-24

* BREAKING
  * Change paths to use woodpecker instead of drone (#494)
  * Move plugin config to root.pipeline.[step].settings (#464)
  * Replace debug with log-level flag (#440)
  * Change prometheus metrics from `drone_*` to `woodpecker_*` (#439)
  * Replace DRONE_ with CI_ variables in pipeline steps (#427)
  * Enable pull_request hook by default on repository activation (#420)
  * Remote Gitea drop basic auth support (#365)
  * Change pipeline config path resolution (#299)
  * Remove push, tag and deployment webhook filters (#281)
  * Clean up config environment variables for server and agent (#218)
* SECURITY
  * Add linter bidichk to prevent malicious utf8 chars (#516)
* FEATURES
  * Show changed files of pipeline in UI (#650)
  * Show yml config of pipeline in UI (#649)
  * Multiarch build for cli and agent docker images (#634), (#622)
  * Get secrets in settings (#604)
  * Add multi-pipeline support to exec & lint (#568)
  * Add repo branches endpoint (#481)
  * Add repo permission endpoint (#436)
  * Add web-config endpoint (#433)
  * Replace www-path with www-proxy option for development (#248)
* BUGFIXES
  * Make gRPC error "too many keepalive pings" only show up in trace logs (#787)
  * WOODPECKER_ENVIRONMENT: ignore items only containing a key and no value (#781)
  * Fix pipeline timestamps (#730)
  * Remove "panic()" as much as possible from code (#682)
  * Send decline events back to UI (#680)
  * Notice all changed files of all related commits for gitea push webhooks (#675)
  * Use global branch filter only on events containing branch info (#659)
  * API GetRepos() return empty list if no active repos exist (#658)
  * Skip nested GitLab repositories during sync (#656), (#652)
  * Build proc tree function should not depend on sorted procs list (#647)
  * Fix sqlite migration on column drop of abnormal schemas (#629)
  * Fix gRPC incompatibility in helm chart (#627)
  * Fix new pipeline not published to UI if protected repo mode enabled (#619)
  * Dont panic, report error back (#582)
  * Improve status updates (#561)
  * Let normal repo admins change timeout to lower values (#543)
  * Fix registry delete (#532)
  * Fix overflowing commit messages (#528)
  * Fix passing of netrc credentials to clone step (#492)
  * Fix various typos (#416)
  * Append trailing slash to default GH API URL (#411)
  * Fix filter pipeline config files (#279)
* ENHANCEMENTS
  * Return better error if repo was deleted/renamed (#780)
  * Add support to set default clone image via environment variable (#769)
  * Add flag to always authenticate when cloning public repositories from locked down / private only forges (#760)
  * UI: show date time on hover over time items (#756)
  * Add repo-link to badge markdown in UI (#753)
  * Allow specifying dind container in values (#750)
  * Add page to view all projects of a user / group (#741)
  * Let non required migration tasks fail and continue (#729)
  * Improve pipeline compiler (#699)
  * Support ChangedFiles for GitHub & Gitlab PRs and pushes and Gitea pushes (#697)
  * Remove unused flags / options (#693)
  * Automatically determine platform of agent (#690)
  * Build ref link point to commit not compare if only one commit was pushed (#673)
  * Hide multi line secrets from log (#671)
  * Do not exclude repo owner from gated rule (#641)
  * Add field for image list in Secrets Repo Settings (Web UI) (#638)
  * Use Woodpecker theme colors on Safari Tab Bar / Header Bar (#632)
  * Add "woodpeckerci/plugin-docker-buildx" to privileged plugins (#623)
  * Use gitlab generic webhooks instead of drone-ci-service (#620)
  * Calculate build number on creation (#615)
  * Hide gin routes logging on non-debug starts (#603)
  * Let remove be a remove (#593)
  * Add flag to set oauth redirect host in dev mode (#586)
  * Add log-level option to cli (#584)
  * Improve favicons (#576)
  * Show icon and index of a pull request in pipelines triggered by pull requests (#575)
  * Improve secrets tab (#574)
  * Use monospace font for build logs (#527)
  * Show environ in every BuildProc (#526)
  * Drop error only on purpose or else report back or log (#514)
  * Migrate database backend to Xorm (#474)
  * Add backend selection for agent (#463)
  * Switch default git plugin (#449)
  * Add log level API (#444)
  * Move entirely to zerolog (#426)
  * Pass context.Context down (#371)
  * Extend Logging & Report to WebHook Caller back if pulls are disabled (#369)
  * If config is no file assume its a folder (#354)
  * Rename cmd agent and server folders and binaries (#330)
  * Release Helm charts (#302)
  * Add flag for specific grpc server addr (#295)
  * Add option to charts, to pass in topology pod constraints (#262)
  * Use server-host as source for public links and warn if it is set to localhost (#251)
  * Rewrite of UI (#245)
* REFACTOR
  * Remove github.com/kr/pretty in favor of assert.EqualValues() (#564)
  * Simplify web router code (#541)
  * Server obtain remote from glob config not from context (#540)
  * Serve index.html directly without template (#539)
  * Add linter revive, unused, ineffassign, varcheck, structcheck, staticcheck, whitespace, misspell (#550), (#551), (#554), (#538), (#537), (#535), (#531), (#530)
  * Rename struct field and add new types into server/model's (#523)
  * Update database in one transaction on syncing user repositories (#513)
  * Format code with 'simplify' flag and check via CI (#509)
  * Use Goblin Assert as intended (#501)
  * Embedding libcompose types for yaml parsing (#495)
  * Use std method to get SystemCertPool (#488)
  * Upgrade urfave/cli to v2 (#483)
  * Remove some wrapper and make code more readable (#478)
  * More logging and refactor (#457)
  * Simplify routes (#437)
  * Move api-routes to separate file (#434)
  * Rename drone-go to woodpecker-go (#390)
  * Remove ghodss/yaml (#384)
  * Move model/ to server/model/ (#366)
  * Use moby definitions for docker pipeline backend (#364)
  * Rewrite Gitlab Remote (#358)
  * Update Generated Proto Code (#351)
  * Remove legacy/unused code + misc cleanups (#331)
  * CLI use version from version/version.go (#329)
  * Move cli/drone/ to cli/ (#329)
  * Cleanup Code (#348)
  * Move cncd/pipeline/pipeline/ to pipeline/ (#347)
  * Move cncd/{logging,pubsub,queue}/ to server/{logging,pubsub,queue}/ (#346)
  * Move remote/ to server/remote/ (#344)
  * Move plugins/ to server/plugins/ (#343)
  * Move store/ to server/store/ (#341)
  * Move router/ to server/router/ (#339)
  * Create agent/ package for backend agnostic logic (#338)
  * Reorganize into server/{api,grpc,shared} packages (#337)
* TESTING
  * Add tests framework for storage migration (#630)
  * Add more golangci-lint linters & sort them (#499) (#502)
  * Compile on pull too (#287)
* DOCUMENTATION
  * Add note about Gitlab & Gitea internal connections to docs (#711)
  * Add registries docs (#679)
  * Add documentation of all agent configuration options (#667)
  * Add `repo` to `when` block (#642)
  * Add development docs (#610)
  * Clarify Docs on Docker for new users in intro (#606)
  * Update Documentation (fix diffs and add settings) (#569)
  * Add notice of supported YAML versions in docs (#556)
  * Update Agent and Pipeline syntax documentation (#506)
  * Update docs about selecting agent based on platform (#470)
  * Add plugin marketplace (for official plugins) (#451)
  * Add search to docs (#448)
  * Add image migration docs (#406)
  * Add security policy (#396)
  * Explain open registration setting (#361)
  * Add json schema and cli lint command (#342)
  * Improve docs deployment (#333)
  * Improve plugin docs (#313)
  * Add Support section to README (#310)
  * Community Guide (#296)
  * Migrate docs framework to Docusaurus (#282)
  * Use woodpecker env variable instead of drone in docker-compose (#264)
* MISC
  * Add support for building in docker (#759)
  * Compile for more platforms on release (#703)
  * Build agent for multiple platforms (arm, arm64, amd64, linux, windows, darwin) (#408)
  * Release deb, rpm bundles (#405)
  * Release cli images (#404)
  * Publish alpine container (#398)
  * Migrate go-docker to docker/docker (#363)
  * Use go's vendoring (#284)

## [v0.14.4](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.14.4) - 2022-01-31

* BUGFIXES
  * Docker Images use golang image for ca-certificates (#608)

## [v0.14.3](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.14.3) - 2021-10-30

* BUGFIXES
  * Add flag for not fetching permissions (FlatPermissions) (#491)
  * Gitea use default branch (#480) (#482)
  * Fix repo access (#476) (#477)
* ENHANCEMENTS
  * Use go embed for web files and remove httptreemux (#382) (#489)

## [v0.14.2](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.14.2) - 2021-10-19

* BUGFIXES
  * Fix sanitizePath (#326) (aa4fa9aab3)
  * Fix json tag for `Pos` at struct `Line` (#422) (#424)
  * Fix channel buffer used with signal.Notify (#421) (#423)
* ENHANCEMENTS
  * Support recursive glob for path conditions (#327) (#412)
* TESTING
  * Add TestPipelineName to procBuilder_test.go (#461) (#455)

## [v0.14.1](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.14.1) - 2021-09-21

* SECURITY
  * Migrate jwt token lib (#332)
* BUGFIXES
  * Increase allowed length for user token in db (#328)
  * Fix cli matrix filter (#311)
  * Fix ignore pushes to tags for gitea (#289)
  * Fix use custom config path to sanitize build names (#280)

## [v0.14.0](https://github.com/woodpecker-ci/woodpecker/releases/tag/v0.14.0) - 2021-08-01

* FEATURES
  * Add OAuth2 Support for Gitea Remote (#226)
  * Add support for path-prefix condition (#174)
* BUGFIXES
  * Allow multi pipeline file to be named .drone.yml (#250)
  * Fix release-server make target by build server with correct option (#237)
  * Fix Gitea unable to login on 0.12.0+ with error "cannot authenticate user. 403 Forbidden" (#221)
* ENHANCEMENTS
  * Update / Remove drone dependencies (#236)
  * Add support to gitea remote for path-prefix condition (#235)
  * Enable go vet for ci (#230)
  * Enforce code format (#228)
  * Add multi-pipeline to Gitea (#225)
  * Move flag definitions into extra files (#215)
  * Remove unused code in server (#213)
  * Docs URL configuration (#206)
  * Filter main branch (#205)
  * Fix multi pipeline bug when a pipeline depends on two other pipelines (#201)
  * Using configured server URL instead of obtained from request (#175)
* DOCUMENTATION
  * Switch in docs to new docker hub image repo (#227)
  * Use WOODPECKER_ env vars in docs (#211)
  * Also show WOODPECKER_HOST and WOODPECKER_SERVER_HOST environment variables in log messages (#208)
  * Move woodpecker to dedicated organisation on github (#202)
* MISC
  * Add chart for installing woodpecker server and agent (#199)
