<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Separator } from '@/components/ui/separator';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { TrendingUp } from 'lucide-vue-next';

const breadcrumbs: BreadcrumbItem[] = [
  { title: 'Dashboard', href: '/dashboard' },
  { title: 'Analytics', href: '/dashboard/analytics' },
];
</script>

<template>
  <AppLayout :breadcrumbs="breadcrumbs">
    <Head title="Dashboard – Analytics" />

    <div class="block sm:flex items-center justify-between px-6 mt-4">
      <div class="flex space-x-1">
        <Button as-child size="sm" variant="ghost"><a href="/dashboard">Overview</a></Button>
        <Button as-child size="sm" variant="default"><a href="/dashboard/analytics">Analytics</a></Button>
        <Button as-child size="sm" variant="ghost"><a href="/dashboard/reports">Reports</a></Button>
      </div>
      <Button variant="outline" size="sm">
        <TrendingUp class="mr-2 h-4 w-4" />
        Export CSV
      </Button>
    </div>

    <Separator class="my-4" />

    <div class="px-6 pb-6 space-y-6">
      <div class="grid gap-4 md:grid-cols-2">
        <Card>
          <CardHeader>
            <CardTitle>Traffic Sources</CardTitle>
            <CardDescription>Top channels driving users</CardDescription>
          </CardHeader>
          <CardContent>
            <ul class="space-y-3 text-sm">
              <li class="flex justify-between"><span>Organic Search</span> <span>54%</span></li>
              <li class="flex justify-between"><span>Direct</span> <span>23%</span></li>
              <li class="flex justify-between"><span>Referral</span> <span>12%</span></li>
              <li class="flex justify-between"><span>Social</span> <span>8%</span></li>
              <li class="flex justify-between"><span>Email</span> <span>3%</span></li>
            </ul>
          </CardContent>
        </Card>
        <Card>
          <CardHeader>
            <CardTitle>Conversion Funnel</CardTitle>
            <CardDescription>Step-by-step conversion rate</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="space-y-3">
              <div class="space-y-1">
                <div class="flex justify-between text-sm"><span>Visited</span><span>10,000</span></div>
                <div class="h-2 rounded bg-muted"><div class="h-2 w-10/12 rounded bg-primary"></div></div>
              </div>
              <div class="space-y-1">
                <div class="flex justify-between text-sm"><span>Signed Up</span><span>2,100</span></div>
                <div class="h-2 rounded bg-muted"><div class="h-2 w-2/12 rounded bg-primary"></div></div>
              </div>
              <div class="space-y-1">
                <div class="flex justify-between text-sm"><span>Converted</span><span>750</span></div>
                <div class="h-2 rounded bg-muted"><div class="h-2 w-[7.5%] rounded bg-primary"></div></div>
              </div>
            </div>
          </CardContent>
        </Card>
      </div>

      <div class="grid gap-4 md:grid-cols-3">
        <Card>
          <CardHeader>
            <CardTitle>Top Pages</CardTitle>
            <CardDescription>Most visited pages</CardDescription>
          </CardHeader>
          <CardContent>
            <ol class="list-decimal pl-5 space-y-1 text-sm">
              <li>/</li>
              <li>/pricing</li>
              <li>/blog/introducing-1-0</li>
              <li>/docs/getting-started</li>
              <li>/dashboard</li>
            </ol>
          </CardContent>
        </Card>
        <Card class="md:col-span-2">
          <CardHeader>
            <CardTitle>Geo Distribution</CardTitle>
            <CardDescription>Top countries by sessions</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="grid grid-cols-2 md:grid-cols-3 gap-3 text-sm">
              <div class="flex justify-between"><span>US</span><span>42%</span></div>
              <div class="flex justify-between"><span>UK</span><span>12%</span></div>
              <div class="flex justify-between"><span>DE</span><span>10%</span></div>
              <div class="flex justify-between"><span>IN</span><span>9%</span></div>
              <div class="flex justify-between"><span>CA</span><span>6%</span></div>
              <div class="flex justify-between"><span>Other</span><span>21%</span></div>
            </div>
          </CardContent>
        </Card>
      </div>
    </div>
  </AppLayout>
</template>

