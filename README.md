# dapodik-progress-pengiriman
Statistik rekapitulasi dapodik progress progress pengiriman tingkat provinsi


## install via composer

- Development snapshot
```bash
$ composer require bantenprov/dapodik-data-progress-pengiriman:dev-master
```
- Latest release:

## download via github
```bash
$ git clone https://github.com/bantenprov/dapodik-data-progress-pengiriman.git
```
#### Edit `config/app.php` :
```php

'providers' => [

    /*
    * Laravel Framework Service Providers...
    */
    Illuminate\Auth\AuthServiceProvider::class,
    Illuminate\Broadcasting\BroadcastServiceProvider::class,
    Illuminate\Bus\BusServiceProvider::class,
    Illuminate\Cache\CacheServiceProvider::class,
    Illuminate\Foundation\Providers\ConsoleSupportServiceProvider::class,
    Illuminate\Cookie\CookieServiceProvider::class,
    //....
    Bantenprov\DDProgressPengiriman\DDProgressPengirimanServiceProvider::class,

```

#### Untuk publish component vue :

```bash
$ php artisan vendor:publish --tag=dd-progress-pengiriman-assets
$ php artisan vendor:publish --tag=dd-progress-pengiriman-public
```
#### Tambahkan route di dalam route : `resources/assets/js/routes.js` :

```javascript
path: '/dashboard',
component: layout('Default'),
children: [
  {
    path: '/dashboard',
    components: {
      main: resolve => require(['./components/views/DashboardHome.vue'], resolve),
      navbar: resolve => require(['./components/Navbar.vue'], resolve),
      sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
    },
    meta: {
      title: "Dashboard"
    }
  },
  //== ...
  {
    path: '/dashboard/dd-progress-pengiriman',
    components: {
        main: resolve => require(['./components/views/bantenprov/dd-progress-pengiriman/DashboardDDProgressPengiriman.vue'], resolve),
        navbar: resolve => require(['./components/Navbar.vue'], resolve),
        sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
    },
    meta: {
        title: "DD Pegawai"
    }
	}
```

```javascript
{
path: '/admin',
redirect: '/admin/dashboard',
component: resolve => require(['./AdminLayout.vue'], resolve),
children: [
//== ...
    {
			path: '/admin/dashboard/dd-progress-pengiriman',
			components: {
				main: resolve => require(['./components/bantenprov/dd-progress-pengiriman/DDProgressPengirimanAdmin.show.vue'], resolve),
				navbar: resolve => require(['./components/Navbar.vue'], resolve),
				sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
			},
			meta: {
				title: "DD Pegawai"
			}
		}
 //== ...   
  ]
},

```
#### Edit menu `resources/assets/js/menu.js`

```javascript
{
  name: 'Dashboard',
  icon: 'fa fa-dashboard',
  childType: 'collapse',
  childItem: [
        {
          name: 'Dashboard',
          link: '/dashboard',
          icon: 'fa fa-angle-double-right'
        },
        {
          name: 'Entity',
          link: '/dashboard/entity',
          icon: 'fa fa-angle-double-right'
        },
        //== ...
        {
          name: 'Angka partisipasi kasar',
          link: '/dashboard/ap-kasar',
          icon: 'fa fa-angle-double-right'
        }
  ]
},
//== ...        
      {
        name: 'Dapodik Data Pegawai',
        link: '/dashboard/dd-progress-pengiriman',
        icon: 'fa fa-angle-double-right'
      },
```

#### Tambahkan components `resources/assets/js/components.js` :

```javascript

//== DD progress-pengiriman

import DDProgressPengiriman from './components/bantenprov/dd-progress-pengiriman/DDProgressPengiriman.chart.vue';
Vue.component('echarts-dd-progress-pengiriman', DDProgressPengiriman);

import DDProgressPengirimanKota from './components/bantenprov/dd-progress-pengiriman/DDProgressPengirimanKota.chart.vue';
Vue.component('echarts-dd-progress-pengiriman-kota', DDProgressPengirimanKota);

import DDProgressPengirimanTahun from './components/bantenprov/dd-progress-pengiriman/DDProgressPengirimanTahun.chart.vue';
Vue.component('echarts-dd-progress-pengiriman-tahun', DDProgressPengirimanTahun);

import DDProgressPengirimanAdminShow from './components/bantenprov/dd-progress-pengiriman/DDProgressPengirimanAdmin.show.vue';
Vue.component('admin-view-dd-progress-pengiriman-tahun', DDProgressPengirimanAdminShow);

//== Echarts DD Pegawai

import DDProgressPengirimanBar01 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanBar01.vue';
Vue.component('dd-progress-pengiriman-bar-01', DDProgressPengirimanBar01);

import DDProgressPengirimanBar02 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanBar02.vue';
Vue.component('dd-progress-pengiriman-bar-02', DDProgressPengirimanBar02);

//== mini bar charts
import DDProgressPengirimanBar03 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanBar03.vue';
Vue.component('dd-progress-pengiriman-bar-03', DDProgressPengirimanBar03);

import DDProgressPengirimanPie01 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanPie01.vue';
Vue.component('dd-progress-pengiriman-pie-01', DDProgressPengirimanPie01);

import DDProgressPengirimanPie02 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanPie02.vue';
Vue.component('dd-progress-pengiriman-pie-02', DDProgressPengirimanPie02);

//== mini pie charts
import DDProgressPengirimanPie03 from './components/views/bantenprov/dd-progress-pengiriman/DDProgressPengirimanPie03.vue';
Vue.component('dd-progress-pengiriman-pie-03', DDProgressPengirimanPie03);
```
