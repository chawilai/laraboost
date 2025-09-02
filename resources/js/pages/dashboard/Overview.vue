<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Button } from '@/components/ui/button';
import { Separator } from '@/components/ui/separator';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { TrendingUp, Users, DollarSign, Activity } from 'lucide-vue-next';

const breadcrumbs: BreadcrumbItem[] = [
  { title: 'Dashboard', href: '/dashboard' },
  { title: 'Overview', href: '/dashboard' },
];

const stats = [
  { title: 'Total Users', value: '2,845', change: '+12.5%', icon: Users },
  { title: 'Revenue', value: '$45,231', change: '+8.2%', icon: DollarSign },
  { title: 'Activity', value: '1,234', change: '+3.1%', icon: Activity },
];

const chartData = [
  { month: 'Jan', value: 400 },
  { month: 'Feb', value: 300 },
  { month: 'Mar', value: 200 },
  { month: 'Apr', value: 278 },
  { month: 'May', value: 189 },
  { month: 'Jun', value: 239 },
];
</script>

<template>
  <AppLayout :breadcrumbs="breadcrumbs">
    <Head title="Dashboard – Overview" />

    <div class="block sm:flex items-center justify-between px-6 mt-4">
      <div class="flex space-x-1">
        <Button as-child size="sm" variant="default"><a href="/dashboard">Overview</a></Button>
        <Button as-child size="sm" variant="ghost"><a href="/dashboard/analytics">Analytics</a></Button>
        <Button as-child size="sm" variant="ghost"><a href="/dashboard/reports">Reports</a></Button>
      </div>
      <Button variant="outline" size="sm">
        <TrendingUp class="mr-2 h-4 w-4" />
        View Report
      </Button>
    </div>

    <Separator class="my-4" />

    <div class="px-6 pb-6 space-y-6">
      <div class="grid gap-4 md:grid-cols-3">
        <Card v-for="stat in stats" :key="stat.title">
          <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle class="text-sm font-medium">{{ stat.title }}</CardTitle>
            <component :is="stat.icon" class="h-4 w-4 text-muted-foreground" />
          </CardHeader>
          <CardContent>
            <div class="text-2xl font-bold">{{ stat.value }}</div>
            <p class="text-xs text-muted-foreground">
              <span class="text-green-600">{{ stat.change }}</span> from last month
            </p>
          </CardContent>
        </Card>
      </div>

      <div class="grid gap-4 md:grid-cols-7">
        <Card class="col-span-4">
          <CardHeader>
            <CardTitle>Overview</CardTitle>
            <CardDescription>Monthly performance chart</CardDescription>
          </CardHeader>
          <CardContent class="pl-2">
            <div class="flex h-[200px] items-end space-x-2">
              <div v-for="data in chartData" :key="data.month" class="flex flex-col items-center space-y-2">
                <div class="bg-primary w-8 rounded-t" :style="{ height: `${(data.value / 400) * 160}px` }"></div>
                <span class="text-xs text-muted-foreground">{{ data.month }}</span>
              </div>
            </div>
          </CardContent>
        </Card>

        <Card class="col-span-3">
          <CardHeader>
            <CardTitle>Recent Activity</CardTitle>
            <CardDescription>Latest user actions</CardDescription>
          </CardHeader>
          <CardContent>
            <div class="space-y-4">
              <div class="flex items-center space-x-4">
                <div class="h-2 w-2 rounded-full bg-blue-500"></div>
                <div class="flex-1 space-y-1">
                  <p class="text-sm font-medium">User registration</p>
                  <p class="text-xs text-muted-foreground">2 minutes ago</p>
                </div>
              </div>
              <div class="flex items-center space-x-4">
                <div class="h-2 w-2 rounded-full bg-green-500"></div>
                <div class="flex-1 space-y-1">
                  <p class="text-sm font-medium">Payment received</p>
                  <p class="text-xs text-muted-foreground">5 minutes ago</p>
                </div>
              </div>
              <div class="flex items-center space-x-4">
                <div class="h-2 w-2 rounded-full bg-orange-500"></div>
                <div class="flex-1 space-y-1">
                  <p class="text-sm font-medium">New order placed</p>
                  <p class="text-xs text-muted-foreground">8 minutes ago</p>
                </div>
              </div>
            </div>
          </CardContent>
        </Card>
      </div>
    </div>
  </AppLayout>

</template>

