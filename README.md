# The PHP Routers Benchmark

[![Software License](https://img.shields.io/badge/License-BSD--3-brightgreen.svg?style=flat-square)](LICENSE)
[![Workflow Status](https://img.shields.io/github/workflow/status/divineniiquaye/php-routers-benchmark/Tests?style=flat-square)](https://github.com/divineniiquaye/php-routers-benchmark/actions?query=workflow%3ATests)
[![Code Maintainability](https://img.shields.io/codeclimate/maintainability/divineniiquaye/php-routers-benchmark?style=flat-square)](https://codeclimate.com/github/divineniiquaye/php-routers-benchmark)
[![Quality Score](https://img.shields.io/scrutinizer/g/divineniiquaye/php-routers-benchmark.svg?style=flat-square)](https://scrutinizer-ci.com/g/divineniiquaye/php-routers-benchmark)
[![Sponsor development of this project](https://img.shields.io/badge/sponsor%20this%20package-%E2%9D%A4-ff69b4.svg?style=flat-square)](https://biurad.com/sponsor)

The intent here is to benchmark and also inventory all popular PHP routing solutions around.

## 📦 Installation & Basic Usage

This project requires [PHP] 7.4 or higher. The recommended way to install, is via [Composer] and [GitHub Ci](https://cli.github.com/) to clone the repo.:

```bash
$ gh repo clone divineniiquaye/php-routers-benchmark
$ cd php-routers-benchmark && composer install
$ php src/benchmark.php
```

## 🧪 Benchmarking Process

The current test creates 100 unique routes with 1 variables placeholder each.

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
- [Rareloop](https://github.com/rareloop/router)
- [AltoRouter](https://github.com/altorouter/altorouter)
- [Nette](https://github.com/nette/routing)
- [Sunrise](https://github.com/sunrise-php/http-router)
- [SpiralRouter](https://github.com/spiral/router)


## ✳️ BenchMark Results

This is a benchmarked results runned on [GitHub Action] with Ubuntu 18, and PHP 7.4.

```
PHP Version: 7.4.14 [Linux] - With XDebug Extension.


################### With Routes Supporting All HTTP Methods ###################



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           75% | █████████████████████████████████████████████                 |
SunriseRouter        62% | ████████████████████████████████████                          |
RareloopRouter       45% | ███████████████████████████                                   |
FastRoute            29% | █████████████████                                             |
Flight Routing       29% | █████████████████                                             |
NetteRouter          28% | █████████████████                                             |
Symfony              19% | ███████████                                                   |
Laravel              19% | ███████████                                                   |


========================== Average Case (static-path) ==========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       73% | ███████████████████████████████████████████                   |
FastRoute            65% | ██████████████████████████████████████                        |
Symfony              43% | █████████████████████████                                     |
AuraRouter           41% | ████████████████████████                                      |
AltoRouter           39% | ███████████████████████                                       |
Laravel              33% | ███████████████████                                           |
NetteRouter          24% | ██████████████                                                |
RareloopRouter       23% | █████████████                                                 |


=========================== Worst Case (static-path) ===========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       96% | █████████████████████████████████████████████████████████     |
FastRoute            85% | ███████████████████████████████████████████████████           |
Symfony              57% | ██████████████████████████████████                            |
Laravel              32% | ███████████████████                                           |
AuraRouter           31% | ██████████████████                                            |
AltoRouter           28% | █████████████████                                             |
NetteRouter          19% | ███████████                                                   |
RareloopRouter       17% | ██████████                                                    |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        92% | ███████████████████████████████████████████████████████       |
AuraRouter           74% | ████████████████████████████████████████████                  |
RareloopRouter       48% | ████████████████████████████                                  |
Flight Routing       40% | ███████████████████████                                       |
Laravel              28% | ████████████████                                              |
FastRoute            23% | █████████████                                                 |
NetteRouter          12% | ███████                                                       |
Symfony              10% | ██████                                                        |


========================= Average Case (dynamic-path) =========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       75% | █████████████████████████████████████████████                 |
AltoRouter           49% | █████████████████████████████                                 |
AuraRouter           44% | ██████████████████████████                                    |
FastRoute            43% | ██████████████████████████                                    |
Laravel              36% | █████████████████████                                         |
RareloopRouter       27% | ████████████████                                              |
Symfony              20% | ████████████                                                  |
NetteRouter          16% | █████████                                                     |


========================== Worst Case (dynamic-path) ==========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing      100% | ███████████████████████████████████████████████████████████   |
FastRoute            59% | ███████████████████████████████████                           |
AltoRouter           37% | ██████████████████████                                        |
Laravel              35% | █████████████████████                                         |
AuraRouter           34% | ████████████████████                                          |
Symfony              27% | ████████████████                                              |
RareloopRouter       22% | ████████████                                                  |
NetteRouter          16% | █████████                                                     |


============================ Best Case (sub-domain) ============================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       64% | ██████████████████████████████████████                        |
Laravel              11% | ██████                                                        |
AuraRouter            7% | ████                                                          |
NetteRouter           5% | ██                                                            |


========================== Average Case (sub-domain) ==========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       64% | ██████████████████████████████████████                        |
Laravel              10% | ██████                                                        |
AuraRouter            6% | ███                                                           |
NetteRouter           4% | ██                                                            |


=========================== Worst Case (sub-domain) ===========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       64% | ██████████████████████████████████████                        |
Laravel              10% | █████                                                         |
AuraRouter            6% | ███                                                           |
NetteRouter           4% | ██                                                            |


############## With Routes Supporting Only A Single HTTP Methods ##############



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
FastRoute            65% | ██████████████████████████████████████                        |
NetteRouter          58% | ██████████████████████████████████                            |
SunriseRouter        52% | ███████████████████████████████                               |
AuraRouter           48% | ████████████████████████████                                  |
RareloopRouter       32% | ███████████████████                                           |
Flight Routing       23% | █████████████                                                 |
Laravel              16% | █████████                                                     |
Symfony              13% | ███████                                                       |


========================== Average Case (static-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           63% | ██████████████████████████████████████                        |
SunriseRouter        52% | ██████████████████████████████                                |
NetteRouter          43% | █████████████████████████                                     |
Flight Routing       35% | ████████████████████                                          |
RareloopRouter       26% | ███████████████                                               |
Symfony              20% | ████████████                                                  |
AuraRouter           19% | ███████████                                                   |
Laravel              18% | ███████████                                                   |


=========================== Worst Case (static-path) ===========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           42% | ████████████████████████                                      |
SunriseRouter        39% | ███████████████████████                                       |
Flight Routing       35% | ████████████████████                                          |
NetteRouter          30% | █████████████████                                             |
Symfony              20% | ████████████                                                  |
RareloopRouter       19% | ███████████                                                   |
Laravel              15% | ████████                                                      |
AuraRouter           11% | ██████                                                        |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        47% | ███████████████████████████                                   |
AuraRouter           44% | ██████████████████████████                                    |
FastRoute            41% | ████████████████████████                                      |
RareloopRouter       25% | ██████████████                                                |
NetteRouter          23% | █████████████                                                 |
Flight Routing       20% | ███████████                                                   |
Laravel              15% | █████████                                                     |
Symfony               5% | ██                                                            |


========================= Average Case (dynamic-path) =========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
FastRoute            98% | ██████████████████████████████████████████████████████████    |
SunriseRouter        67% | ███████████████████████████████████████                       |
Flight Routing       46% | ███████████████████████████                                   |
NetteRouter          39% | ███████████████████████                                       |
RareloopRouter       36% | █████████████████████                                         |
AuraRouter           25% | ███████████████                                               |
Laravel              25% | ███████████████                                               |
Symfony              12% | ███████                                                       |


========================== Worst Case (dynamic-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           66% | ███████████████████████████████████████                       |
SunriseRouter        48% | ████████████████████████████                                  |
Flight Routing       45% | ██████████████████████████                                    |
NetteRouter          31% | ██████████████████                                            |
RareloopRouter       26% | ███████████████                                               |
Laravel              19% | ███████████                                                   |
AuraRouter           15% | ████████                                                      |
Symfony              12% | ███████                                                       |


============================ Best Case (sub-domain) ============================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       64% | ██████████████████████████████████████                        |
Laravel              18% | ██████████                                                    |
NetteRouter          15% | ████████                                                      |
AuraRouter            7% | ████                                                          |


========================== Average Case (sub-domain) ==========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       64% | ██████████████████████████████████████                        |
Laravel              18% | ██████████                                                    |
NetteRouter          14% | ████████                                                      |
AuraRouter            6% | ███                                                           |


=========================== Worst Case (sub-domain) ===========================

Symfony             100% | ████████████████████████████████████████████████████████████  |
Flight Routing       65% | ██████████████████████████████████████                        |
Laravel              18% | ██████████                                                    |
NetteRouter          14% | ████████                                                      |
AuraRouter            6% | ███                                                           |
```

[PHP]: https://php.net
[Composer]: https://getcomposer.org
[GitHub Action]: https://github.com/divineniiquaye/php-routers-benchmark/runs/1734147863
