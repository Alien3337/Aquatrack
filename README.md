# Aquatrack
import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Progress } from "@/components/ui/progress"; import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs"; import { Bell, Droplet, BarChart3, Settings } from "lucide-react";

export default function AquaTrackApp() { const [usage, setUsage] = useState({ bathroom: 45, kitchen: 30, laundry: 25 });

const totalUsage = Object.values(usage).reduce((acc, val) => acc + val, 0);

return ( <div className="p-4 max-w-md mx-auto"> <h1 className="text-2xl font-bold text-center mb-4 text-blue-700">AquaTrack</h1> <Tabs defaultValue="home"> <TabsList className="grid grid-cols-4 gap-1 mb-4"> <TabsTrigger value="home"><Droplet size={20} /></TabsTrigger> <TabsTrigger value="stats"><BarChart3 size={20} /></TabsTrigger> <TabsTrigger value="alerts"><Bell size={20} /></TabsTrigger> <TabsTrigger value="settings"><Settings size={20} /></TabsTrigger> </TabsList>

<TabsContent value="home">
      <Card>
        <CardContent className="p-4">
          <h2 className="text-lg font-semibold mb-2">Today's Total Usage: {totalUsage} L</h2>
          <div className="space-y-2">
            <div>
              <span>Bathroom: {usage.bathroom} L</span>
              <Progress value={(usage.bathroom / totalUsage) * 100} />
            </div>
            <div>
              <span>Kitchen: {usage.kitchen} L</span>
              <Progress value={(usage.kitchen / totalUsage) * 100} />
            </div>
            <div>
              <span>Laundry: {usage.laundry} L</span>
              <Progress value={(usage.laundry / totalUsage) * 100} />
            </div>
          </div>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="stats">
      <Card>
        <CardContent className="p-4 text-sm text-gray-600">
          <p>Weekly and monthly water usage graphs coming soon...</p>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="alerts">
      <Card>
        <CardContent className="p-4 text-sm text-gray-600">
          <p>No alerts. You're using water efficiently!</p>
        </CardContent>
      </Card>
    </TabsContent>

    <TabsContent value="settings">
      <Card>
        <CardContent className="p-4">
          <p className="text-sm text-gray-600">Settings panel for notifications and preferences (coming soon).</p>
          <Button className="mt-2">Update Preferences</Button>
        </CardContent>
      </Card>
    </TabsContent>
  </Tabs>
</div>

); }
