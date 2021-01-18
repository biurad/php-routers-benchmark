# The PHP Routers Benchmark

[![Software License](https://img.shields.io/badge/License-BSD--3-brightgreen.svg?style=flat-square)](LICENSE)
[![Workflow Status](https://img.shields.io/github/workflow/status/divineniiquaye/php-routers-benchmark/Tests?style=flat-square)](https://github.com/divineniiquaye/php-routers-benchmark/actions?query=workflow%3ATests)
[![Code Maintainability](https://img.shields.io/codeclimate/maintainability/divineniiquaye/php-routers-benchmark?style=flat-square)](https://codeclimate.com/github/divineniiquaye/php-routers-benchmark)
[![Quality Score](https://img.shields.io/scrutinizer/g/divineniiquaye/php-routers-benchmark.svg?style=flat-square)](https://scrutinizer-ci.com/g/divineniiquaye/php-routers-benchmark)
[![Sponsor development of this project](https://img.shields.io/badge/sponsor%20this%20package-%E2%9D%A4-ff69b4.svg?style=flat-square)](https://biurad.com/sponsor)

The intent here is to benchmark and also inventory all popular PHP routing solutions around.

## 📦 Installation & Basic Usage

This project requires [PHP] 7.4 or higher. The recommended way to install, is via [Composer]. Simply run:

```bash
$ composer require divineniiquaye/php-routers-benchmark
```

## 🧪 Benchmarking Process

The current test creates 100 unique routes with 3 variables placeholder each.

Example of route: `/controller1/action1/{world}`

This benchmarking will be runned on the following three different situations for both path & subdomain:

- the best case (i.e when a request matches the first route for all differents HTTP method)
- the worst case (i.e when a request matches the last route for all differents HTTP method)
- the average case (i.e the mean which is probably the most realistic test).

And all tests will be runned using the following sets of routes:

- in the first set all routes matches all HTTP methods.
- in the second set all routes matches only a single HTTP method.

The benchmarked routing implementations are:

- [Flight Routing](https://github.com/divineniiquaye/flight-routing)
- [FastRoute](https://github.com/nikic/FastRoute)
- [Symfony](https://github.com/symfony/routing)
- [Laravel](https://github.com/illuminate/routing)
- [Aura3](https://github.com/auraphp/Aura.Router)
- [Pecee](https://github.com/pecee/simple-router)
- [Rareloop](https://github.com/rareloop/router)
- [AltoRouter](https://github.com/altorouter/altorouter)
- [Nette](https://github.com/nette/routing)


## ✳️ BenchMark Results

This is a benchmarked results runned on [GitHub Action](https://github.com/divineniiquaye/php-routers-benchmark/runs/1722212650) with Ubuntu 18, and PHP 8.

```
PHP Version: 8.0.0 [Linux] - With XDebug Extension.


################### With Routes Supporting All HTTP Methods ###################



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           77% | ██████████████████████████████████████████████                |
RareloopRouter       45% | ███████████████████████████                                   |
FastRoute            28% | █████████████████                                             |
Flight Routing       28% | ████████████████                                              |
NetteRouter          27% | ████████████████                                              |
Laravel              18% | ███████████                                                   |
Symfony              18% | ██████████                                                    |


========================== Average Case (static-path) ==========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
FastRoute            91% | ██████████████████████████████████████████████████████        |
Symfony              59% | ███████████████████████████████████                           |
AuraRouter           58% | ██████████████████████████████████                            |
AltoRouter           53% | ███████████████████████████████                               |
Laravel              43% | █████████████████████████                                     |
NetteRouter          31% | ██████████████████                                            |
RareloopRouter       30% | █████████████████                                             |


=========================== Worst Case (static-path) ===========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
FastRoute            88% | ████████████████████████████████████████████████████          |
Symfony              59% | ███████████████████████████████████                           |
AuraRouter           33% | ███████████████████                                           |
Laravel              33% | ███████████████████                                           |
AltoRouter           28% | ████████████████                                              |
NetteRouter          20% | ███████████                                                   |
RareloopRouter       17% | ██████████                                                    |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           77% | ██████████████████████████████████████████████                |
RareloopRouter       36% | █████████████████████                                         |
Flight Routing       28% | █████████████████                                             |
Laravel              22% | █████████████                                                 |
FastRoute            16% | █████████                                                     |
NetteRouter           9% | █████                                                         |
Symfony               7% | ████                                                          |


========================= Average Case (dynamic-path) =========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
AltoRouter           61% | ████████████████████████████████████                          |
FastRoute            57% | ██████████████████████████████████                            |
AuraRouter           56% | █████████████████████████████████                             |
Laravel              47% | ████████████████████████████                                  |
RareloopRouter       35% | ████████████████████                                          |
Symfony              26% | ███████████████                                               |
NetteRouter          20% | ████████████                                                  |


========================== Worst Case (dynamic-path) ==========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
FastRoute            56% | █████████████████████████████████                             |
AltoRouter           35% | ████████████████████                                          |
Laravel              34% | ████████████████████                                          |
AuraRouter           34% | ████████████████████                                          |
Symfony              25% | ███████████████                                               |
RareloopRouter       21% | ████████████                                                  |
NetteRouter          15% | █████████                                                     |


============================ Best Case (sub-domain) ============================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       70% | ██████████████████████████████████████████                    |
Laravel              11% | ██████                                                        |
AuraRouter            7% | ████                                                          |
NetteRouter           5% | ██                                                            |


========================== Average Case (sub-domain) ==========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       71% | ██████████████████████████████████████████                    |
Laravel              11% | ██████                                                        |
AuraRouter            7% | ███                                                           |
NetteRouter           4% | ██                                                            |


=========================== Worst Case (sub-domain) ===========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       73% | ███████████████████████████████████████████                   |
Laravel              11% | ██████                                                        |
AuraRouter            6% | ███                                                           |
NetteRouter           4% | ██                                                            |


############## With Routes Supporting Only A Single HTTP Methods ##############



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
FastRoute            65% | ██████████████████████████████████████                        |
NetteRouter          57% | ██████████████████████████████████                            |
AuraRouter           49% | █████████████████████████████                                 |
RareloopRouter       32% | ███████████████████                                           |
Flight Routing       23% | █████████████                                                 |
Laravel              16% | █████████                                                     |
Symfony              13% | ███████                                                       |


========================== Average Case (static-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           63% | █████████████████████████████████████                         |
NetteRouter          44% | ██████████████████████████                                    |
Flight Routing       35% | █████████████████████                                         |
RareloopRouter       26% | ███████████████                                               |
Symfony              20% | ████████████                                                  |
Laravel              19% | ███████████                                                   |
AuraRouter           19% | ███████████                                                   |


=========================== Worst Case (static-path) ===========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           41% | ████████████████████████                                      |
Flight Routing       35% | ████████████████████                                          |
NetteRouter          30% | ██████████████████                                            |
Symfony              20% | ████████████                                                  |
RareloopRouter       18% | ███████████                                                   |
Laravel              15% | █████████                                                     |
AuraRouter           11% | ██████                                                        |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           44% | ██████████████████████████                                    |
FastRoute            41% | ████████████████████████                                      |
RareloopRouter       25% | ███████████████                                               |
NetteRouter          23% | █████████████                                                 |
Flight Routing       20% | ███████████                                                   |
Laravel              16% | █████████                                                     |
Symfony               5% | ██                                                            |


========================= Average Case (dynamic-path) =========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
FastRoute            98% | ██████████████████████████████████████████████████████████    |
Flight Routing       47% | ████████████████████████████                                  |
NetteRouter          39% | ███████████████████████                                       |
RareloopRouter       37% | ██████████████████████                                        |
Laravel              26% | ███████████████                                               |
AuraRouter           26% | ███████████████                                               |
Symfony              12% | ███████                                                       |


========================== Worst Case (dynamic-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           65% | ██████████████████████████████████████                        |
Flight Routing       47% | ████████████████████████████                                  |
NetteRouter          32% | ██████████████████                                            |
RareloopRouter       27% | ████████████████                                              |
Laravel              19% | ███████████                                                   |
AuraRouter           15% | █████████                                                     |
Symfony              12% | ██████                                                        |


============================ Best Case (sub-domain) ============================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       72% | ███████████████████████████████████████████                   |
Laravel              19% | ███████████                                                   |
NetteRouter          15% | █████████                                                     |
AuraRouter            7% | ████                                                          |


========================== Average Case (sub-domain) ==========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       72% | ███████████████████████████████████████████                   |
Laravel              18% | ██████████                                                    |
NetteRouter          13% | ███████                                                       |
AuraRouter            6% | ███                                                           |


=========================== Worst Case (sub-domain) ===========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       72% | ██████████████████████████████████████████                    |
Laravel              18% | ██████████                                                    |
NetteRouter          15% | ████████                                                      |
AuraRouter            6% | ███                                                           |
```

[PHP]: https://php.net
[Composer]: https://getcomposer.org
