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

The current test creates 110 - 300 unique routes with 1 variables placeholder each.

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
PHP Version: 7.4.14 [Linux fv-az50-210 5.4.0-1039-azure #41~18.04.1-Ubuntu SMP x86_64] - With XDebug Extension.


################### With Routes Supporting All HTTP Methods ###################



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           95% | █████████████████████████████████████████████████████████     |
SunriseRouter        85% | ██████████████████████████████████████████████████            |
RareloopRouter       54% | ████████████████████████████████                              |
Flight Routing       50% | █████████████████████████████                                 |
FastRoute            36% | █████████████████████                                         |
SpiralRouter         34% | ████████████████████                                          |
NetteRouter          31% | ██████████████████                                            |
Laravel              23% | █████████████                                                 |
Symfony              23% | █████████████                                                 |


========================== Average Case (static-path) ==========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       91% | ██████████████████████████████████████████████████████        |
FastRoute            66% | ███████████████████████████████████████                       |
SpiralRouter         50% | █████████████████████████████                                 |
Symfony              42% | █████████████████████████                                     |
AuraRouter           41% | ████████████████████████                                      |
AltoRouter           36% | █████████████████████                                         |
Laravel              32% | ███████████████████                                           |
NetteRouter          23% | ██████████████                                                |
RareloopRouter       22% | █████████████                                                 |


=========================== Worst Case (static-path) ===========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        78% | ██████████████████████████████████████████████                |
FastRoute            72% | ███████████████████████████████████████████                   |
Symfony              47% | ███████████████████████████                                   |
SpiralRouter         42% | █████████████████████████                                     |
Laravel              26% | ███████████████                                               |
AuraRouter           25% | ███████████████                                               |
AltoRouter           22% | █████████████                                                 |
NetteRouter          16% | █████████                                                     |
RareloopRouter       14% | ████████                                                      |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
AuraRouter           94% | ████████████████████████████████████████████████████████      |
SunriseRouter        84% | ██████████████████████████████████████████████████            |
RareloopRouter       45% | ██████████████████████████                                    |
SpiralRouter         36% | █████████████████████                                         |
Flight Routing       33% | ███████████████████                                           |
Laravel              23% | █████████████                                                 |
FastRoute            17% | ██████████                                                    |
NetteRouter          11% | ██████                                                        |
Symfony               7% | ████                                                          |


========================= Average Case (dynamic-path) =========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       74% | ████████████████████████████████████████████                  |
SpiralRouter         55% | █████████████████████████████████                             |
AltoRouter           44% | ██████████████████████████                                    |
AuraRouter           43% | █████████████████████████                                     |
FastRoute            42% | █████████████████████████                                     |
Laravel              33% | ███████████████████                                           |
RareloopRouter       26% | ███████████████                                               |
Symfony              17% | ██████████                                                    |
NetteRouter          15% | █████████                                                     |


========================== Worst Case (dynamic-path) ==========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
SunriseRouter       100% | ███████████████████████████████████████████████████████████   |
SpiralRouter         62% | ████████████████████████████████████                          |
FastRoute            61% | ████████████████████████████████████                          |
AltoRouter           35% | █████████████████████                                         |
Laravel              35% | █████████████████████                                         |
AuraRouter           35% | ████████████████████                                          |
Symfony              25% | ███████████████                                               |
RareloopRouter       22% | ████████████                                                  |
NetteRouter          16% | █████████                                                     |


============================ Best Case (sub-domain) ============================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       95% | █████████████████████████████████████████████████████████     |
Symfony              52% | ███████████████████████████████                               |
Laravel              21% | ████████████                                                  |
AuraRouter           18% | ██████████                                                    |
NetteRouter          10% | ██████                                                        |


========================== Average Case (sub-domain) ==========================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing      100% | ███████████████████████████████████████████████████████████   |
Symfony              56% | █████████████████████████████████                             |
Laravel              22% | █████████████                                                 |
AuraRouter           17% | ██████████                                                    |
NetteRouter          10% | ██████                                                        |


=========================== Worst Case (sub-domain) ===========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        86% | ███████████████████████████████████████████████████           |
Symfony              58% | ██████████████████████████████████                            |
Laravel              22% | █████████████                                                 |
AuraRouter           16% | █████████                                                     |
NetteRouter          10% | █████                                                         |


############## With Routes Supporting Only A Single HTTP Methods ##############



=========================== Best Case (static-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
FastRoute            63% | █████████████████████████████████████                         |
NetteRouter          59% | ███████████████████████████████████                           |
SunriseRouter        55% | █████████████████████████████████                             |
AuraRouter           55% | ████████████████████████████████                              |
RareloopRouter       33% | ███████████████████                                           |
Flight Routing       28% | ████████████████                                              |
SpiralRouter         22% | █████████████                                                 |
Laravel              16% | █████████                                                     |
Symfony              12% | ███████                                                       |


========================== Average Case (static-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           62% | ████████████████████████████████████                          |
SunriseRouter        49% | █████████████████████████████                                 |
NetteRouter          44% | ██████████████████████████                                    |
Flight Routing       44% | ██████████████████████████                                    |
RareloopRouter       26% | ███████████████                                               |
SpiralRouter         24% | ██████████████                                                |
Symfony              20% | ███████████                                                   |
AuraRouter           19% | ███████████                                                   |
Laravel              18% | ██████████                                                    |


=========================== Worst Case (static-path) ===========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
Flight Routing       44% | ██████████████████████████                                    |
AltoRouter           39% | ███████████████████████                                       |
SunriseRouter        30% | ██████████████████                                            |
NetteRouter          28% | █████████████████                                             |
Symfony              20% | ███████████                                                   |
RareloopRouter       18% | ██████████                                                    |
SpiralRouter         16% | █████████                                                     |
Laravel              14% | ████████                                                      |
AuraRouter           11% | ██████                                                        |


=========================== Best Case (dynamic-path) ===========================

AltoRouter          100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        57% | ██████████████████████████████████                            |
AuraRouter           56% | █████████████████████████████████                             |
FastRoute            46% | ███████████████████████████                                   |
RareloopRouter       30% | █████████████████                                             |
NetteRouter          27% | ████████████████                                              |
SpiralRouter         24% | ██████████████                                                |
Flight Routing       24% | ██████████████                                                |
Laravel              16% | █████████                                                     |
Symfony               5% | ███                                                           |


========================= Average Case (dynamic-path) =========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           98% | ██████████████████████████████████████████████████████████    |
SunriseRouter        67% | ████████████████████████████████████████                      |
Flight Routing       49% | █████████████████████████████                                 |
NetteRouter          42% | █████████████████████████                                     |
RareloopRouter       38% | ██████████████████████                                        |
SpiralRouter         37% | ██████████████████████                                        |
AuraRouter           27% | ████████████████                                              |
Laravel              25% | ██████████████                                                |
Symfony              11% | ██████                                                        |


========================== Worst Case (dynamic-path) ==========================

FastRoute           100% | ████████████████████████████████████████████████████████████  |
AltoRouter           64% | ██████████████████████████████████████                        |
SunriseRouter        47% | ████████████████████████████                                  |
Flight Routing       46% | ███████████████████████████                                   |
NetteRouter          34% | ████████████████████                                          |
SpiralRouter         29% | █████████████████                                             |
RareloopRouter       27% | ████████████████                                              |
Laravel              20% | ███████████                                                   |
AuraRouter           16% | █████████                                                     |
Symfony              11% | ██████                                                        |


============================ Best Case (sub-domain) ============================

SunriseRouter       100% | ████████████████████████████████████████████████████████████  |
Flight Routing       91% | ██████████████████████████████████████████████████████        |
Symfony              52% | ███████████████████████████████                               |
NetteRouter          32% | ███████████████████                                           |
Laravel              29% | █████████████████                                             |
AuraRouter           16% | █████████                                                     |


========================== Average Case (sub-domain) ==========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        98% | ██████████████████████████████████████████████████████████    |
Symfony              57% | ██████████████████████████████████                            |
NetteRouter          34% | ████████████████████                                          |
Laravel              32% | ███████████████████                                           |
AuraRouter           16% | █████████                                                     |


=========================== Worst Case (sub-domain) ===========================

Flight Routing      100% | ████████████████████████████████████████████████████████████  |
SunriseRouter        98% | ██████████████████████████████████████████████████████████    |
Symfony              57% | ██████████████████████████████████                            |
NetteRouter          34% | ████████████████████                                          |
Laravel              32% | ███████████████████                                           |
AuraRouter           16% | █████████                                                     |


############## With Routes Supporting All HTTP Methods And Cache ##############



=========================== Best Case (static-path) ===========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       83% | ██████████████████████████████████████████████████            |


========================== Average Case (static-path) ==========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       76% | █████████████████████████████████████████████                 |


=========================== Worst Case (static-path) ===========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       75% | ████████████████████████████████████████████                  |


=========================== Best Case (dynamic-path) ===========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       56% | █████████████████████████████████                             |


========================= Average Case (dynamic-path) =========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       45% | ██████████████████████████                                    |


========================== Worst Case (dynamic-path) ==========================

Symfony        100% | ████████████████████████████████████████████████████████████  |
FastRoute       44% | ██████████████████████████                                    |


============================ Best Case (sub-domain) ============================

Symfony      100% | ████████████████████████████████████████████████████████████  |


========================== Average Case (sub-domain) ==========================

Symfony      100% | ████████████████████████████████████████████████████████████  |


=========================== Worst Case (sub-domain) ===========================

Symfony      100% | ████████████████████████████████████████████████████████████  |
```

[PHP]: https://php.net
[Composer]: https://getcomposer.org
[GitHub Action]: https://github.com/divineniiquaye/php-routers-benchmark/runs/1867573092?check_suite_focus=true
