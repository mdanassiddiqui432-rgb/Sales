import React, { useState, useEffect } from "react";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";
import { Plus, Trash2, LogOut } from "lucide-react";
import { createClient } from "@supabase/supabase-js";

/*
ENTERPRISE PRIVATE CRM VERSION

✅ Private Login (Supabase Auth - Email Login)
✅ Cloud Database (Shared across company users)
✅ 50 Day Expiry Notification
✅ Inline Excel Style Entry

⚠️ IMPORTANT:
Replace below with your Supabase project keys
*/

const supabaseUrl = "https://sgdceuczipawqrxtafec.supabase.co";
const supabaseAnonKey = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InNnZGNldWN6aXBhd3FyeHRhZmVjIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzA2MjY2MTEsImV4cCI6MjA4NjIwMjYxMX0.9lwe5oSmOlX-Nvl7lhfTY__FBSj7wVH8KbM5TLQOHCQ";

const supabase = createClient(supabaseUrl, supabaseAnonKey);

export default function SalesTrackerCRM() {
  const [session, setSession] = useState(null);
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [deals, setDeals] = useState([]);

  const [newDeal, setNewDeal] = useState({
    entity: "",
    customerName: "",
    customerPO: "",
    poDate: "",
    startDate: "",
    validity: "",
    renewalStatus: "",
    supplyService: "",
    description: "",
    location: "",
    valueExcl: "",
    valueIncl: "",
    remarks: "",
  });

  /* ================= AUTH ================= */

  useEffect(() => {
    supabase.auth.getSession().then(({ data }) => {
      setSession(data.session);
    });

    const { data: listener } = supabase.auth.onAuthStateChange((_e, s) => {
      setSession(s);
    });

    return () => listener.subscription.unsubscribe();
  }, []);

  const signIn = async () => {
    await supabase.auth.signInWithPassword({ email, password });
  };

  const signOut = async () => {
    await supabase.auth.signOut();
  };

  /* ================= DATA LOAD ================= */

  const loadDeals = async () => {
    const { data } = await supabase.from("proposals").select("*").order("id", { ascending: false });
    if (data) setDeals(data);
  };

  useEffect(() => {
    if (session) loadDeals();
  }, [session]);

  /* ================= NOTIFICATION ================= */

  useEffect(() => {
    if ("Notification" in window) Notification.requestPermission();
  }, []);

  useEffect(() => {
    const today = new Date();

    deals.forEach((deal) => {
      if (!deal.validity) return;

      const expiryDate = new Date(deal.validity);
      const diffDays = Math.ceil((expiryDate - today) / (1000 * 60 * 60 * 24));

      if (diffDays <= 50 && diffDays >= 0 && !deal.notified) {
        if (Notification.permission === "granted") {
          new Notification("Proposal Expiry Alert", {
            body: `${deal.customername} expires in ${diffDays} days`,
          });
        }
      }
    });
  }, [deals]);

  /* ================= CRUD ================= */

  const addDeal = async () => {
    if (!newDeal.customerName) return;

    await supabase.from("proposals").insert([
      {
        ...newDeal,
      },
    ]);

    setNewDeal({
      entity: "",
      customerName: "",
      customerPO: "",
      poDate: "",
      startDate: "",
      validity: "",
      renewalStatus: "",
      supplyService: "",
      description: "",
      location: "",
      valueExcl: "",
      valueIncl: "",
      remarks: "",
    });

    loadDeals();
  };

  const deleteDeal = async (id) => {
    await supabase.from("proposals").delete().eq("id", id);
    loadDeals();
  };

  /* ================= LOGIN SCREEN ================= */

  if (!session) {
    return (
      <div className="h-screen flex items-center justify-center">
        <Card className="w-96">
          <CardHeader>
            <CardTitle>Company Private CRM Login</CardTitle>
          </CardHeader>
          <CardContent className="grid gap-3">
            <Input placeholder="Email" value={email} onChange={(e) => setEmail(e.target.value)} />
            <Input type="password" placeholder="Password" value={password} onChange={(e) => setPassword(e.target.value)} />
            <Button onClick={signIn}>Login</Button>
          </CardContent>
        </Card>
      </div>
    );
  }

  /* ================= MAIN CRM ================= */

  return (
    <div className="p-6 grid gap-6">
      <div className="flex justify-between items-center">
        <motion.h1 initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="text-2xl font-bold">
          Private Sales Proposal Tracker
        </motion.h1>
        <Button variant="outline" onClick={signOut} className="flex gap-2">
          <LogOut size={16} /> Logout
        </Button>
      </div>

      <Card>
        <CardHeader>
          <CardTitle>Add Proposal (Inline)</CardTitle>
        </CardHeader>
        <CardContent className="overflow-x-auto">
          <div className="flex gap-2 min-w-max">
            {Object.keys(newDeal).map((field) => (
              <Input
                key={field}
                placeholder={field}
                className="w-40"
                type={field.toLowerCase().includes("date") || field === "validity" ? "date" : "text"}
                value={newDeal[field]}
                onChange={(e) => setNewDeal({ ...newDeal, [field]: e.target.value })}
              />
            ))}
            <Button onClick={addDeal}>
              <Plus size={16} /> Add
            </Button>
          </div>
        </CardContent>
      </Card>

      <Card>
        <CardHeader>
          <CardTitle>All Proposals</CardTitle>
        </CardHeader>
        <CardContent className="overflow-x-auto">
          <table className="min-w-full text-sm">
            <thead>
              <tr className="border-b font-semibold text-left">
                {Object.keys(newDeal).map((key) => (
                  <th key={key} className="p-2 capitalize">{key}</th>
                ))}
                <th className="p-2">Action</th>
              </tr>
            </thead>
            <tbody>
              {deals.map((deal) => (
                <tr key={deal.id} className="border-b">
                  {Object.keys(newDeal).map((key) => (
                    <td key={key} className="p-2">{deal[key.toLowerCase()] || deal[key]}</td>
                  ))}
                  <td className="p-2">
                    <Button size="sm" variant="destructive" onClick={() => deleteDeal(deal.id)}>
                      <Trash2 size={14} />
                    </Button>
                  </td>
                </tr>
              ))}
            </tbody>
          </table>
        </CardContent>
      </Card>
    </div>
  );
}
